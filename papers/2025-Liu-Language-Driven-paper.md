# <Paper Title>

<!--
  Copy this file, then fill in every section. Do not delete section headings;
  mark fields you cannot answer as `N/A` and explain in one sentence.
  Filename convention: <first-author-last-name>-<year>-<keyword>.md
  Cross-link this file from the relevant taxonomy pages and from INDEX.md.
-->

## Citation

- **Authors**: Yibo Liu, Liam Shatzel, Brandon Haworth, Teseo Schneider
- **Year**: 2025
- **Venue**: arXiv preprint arXiv:2508.15047
- **DOI / Link**: https://arxiv.org/abs/2508.15047
- **BibTeX key**: liu2025llmguided

## Research Problem

We observe that human navigation and movement in crowds are often influenced by complex social and environmental interactions, 
driven mainly by language and dialogue. 
However, most existing work does not consider these dimensions and leads to animations 
where agentagent and agent-environment interactions are largely limited to steering and fixed higher-level goal extrapolation.

## Core Idea

We propose a novel method that exploits large language models (LLMs) to control agents’ movement. 
Our method has two main components: a dialogue system and language-driven navigation. 
We periodically query agent-centric LLMs conditioned on character personalities, roles, desires, and relationships 
to control the generation of inter-agent dialogue when necessitated by the spatial and social relationships with neighbouring agents. 
We then use the conversation and each agent’s personality, emotional state, vision, 
and physical state to control the navigation and steering of each agent.

## Method

- **Input**: 
- Global state $S$: environment description, list of locations, and possible goals (names and positions).
  - For each agent $a_i$:
    - Profile $P_i$: ID and personality (MBTI).
    - Friend list $F_i = {f_i^j | j = 1..m}$.
    - State $s_i$ (empty initially).
    - Location $\ell_i$.
    - Perception $p_i$.
    - Motion parameters $m_i$.
    - History $h_i$: past $k = 50$ events (timestamp + position/dialog/vision/movement).
  - Current time $t$.
- **Representation**: 
- Static parts: $P_i$, $F_i$.
  - Motion parts: $m_i = { g_i, d_i }$.
    - $g_i$: current goal (randomly initialized).
    - $d_i = { \gamma_i, \phi_i, \kappa_i, \alpha_i, \kappa_i^n, \rho_i, f_i^{max}, v_i^{max} }$.
      - $\gamma_i$: path-following.
      - $\phi_i$: PAM avoidance.
      - $\kappa_i$: cohesion.
      - $\alpha_i$: alignment.
      - $\rho_i$: separation.
      - $\kappa_i^n$: cohesion neighbors.
      - $f_i^{max}$: maximum force.
      - $v_i^{max}$: maximum speed.
  - Perception: $p_i = { I_i, dialog }$, where $I_i$ is the rendered first-person vision image.
  - History: $h_i$ chronologically stores timestamps and updated actions.
- **Model / Algorithm**:
1. Query LLMs every $k = 100$ frames.
  2. Use $A^*$ + string pulling to generate waypoints.
  3. Update location and velocity using predictive force-based steering combining boids and PAM:
     - Path-following, cohesion, alignment, separation, and obstacle forces.
     - Total force $F_i = \min(f_i^{max}, f_i^\gamma + f_i^\kappa + f_i^\alpha + f_i^\rho + f_i^o)$.
     - Explicit integration updates $v_i^{t+1}$ and $\ell_i^{t+1}$.
  4. Update perception:
     - Render $I_i$.
     - Group agents within 1.5 m, with maximum group size $g_{max} = 6$.
     - Dialogue system takes $t$, $S$, and each $a_k$ in the group, and outputs an ordered list of $(agent\ id, dialog)$ pairs.
  5. Language-driven movement:
     - Takes $a_i$, $t$, and $S$.
     - Decides whether to change $g_i$, update $m_i$, or continue in the current state.
     - Produces new state $s_i'$.
     - Generates a decision summary appended to $h_i$.
     - Generates a short description of $I_i$, also appended to $h_i$.
- **Output**: 
- Per agent: updated $m_i$, $s_i$, $h_i$, dialogue, $\ell_i^{t+1}$, and $v_i^{t+1}$.
  - Crowd level: emergent grouping/ungrouping, gathering, and dialogue-driven information propagation.

## Semantic Level

<!-- Pick exactly one primary, optionally list secondary. -->

- [ ] Low-level (trajectories / velocity / motion primitives)
- [ ] Mid-level (activities / navigation goals / interaction rules)
- [√] High-level (natural language / social intention / world knowledge)

**Why:** Because in this paper, agents' motion decisions are driven by 
LLM-generated dialogue, personality, social relationships, emotional state, and world knowledge. And these belong to high-level.

## Generation Mechanism

<!-- Pick exactly one primary, optionally list secondary. -->

- [ ] Rule-based simulation
- [ ] Data-driven learning (supervised / imitation)
- [ ] Neural behaviour generation (RL / VAE / GAN)
- [ ] Generative models (diffusion / transformer for behaviour)
- [√] LLM-based agents
- [ ] Multi-agent systems

**Why:** LLMs produce dialogue and make navigation/steering decisions conditioned on personality, emotion, relationships, vision, and history.

## Simulation Target

- [ ] Individual virtual human
- [ ] Small groups (2–10)
- [√] Dense crowds (tens–hundreds)
- [ ] Large-scale virtual worlds (thousands+)
- [ ] Urban environments

**Why:** There were 50 agents in the university scene and 30 agents in the museum scene.

## Crowd Simulation Aspect

- **Individual behaviour**:
  Each agent has a predefined unique personality, background, etc.,and moves within the crowd.
  It communicates with other agents through generated language dialogue that matches its individual traits,
  and this dialogue influences its own motion and goals.
- **Group behaviour**:
  Agents within 1.5 m of each other form a small group that can converse,
  and dialogue is generated. The dialogue changes individual trajectories and ultimately shapes the group's movement trajectory and trends.
  The maximum group size is 6, and an LLM is also used to decide who is suitable to join the group.
- **Emergent behaviour**:
  Unpredictable events occur in the experiments, such as free T-shirt distribution and a damaged painting in a museum.
  Agents judge their own reactions to emergency events based on their personality settings and communication with other agents,
  resulting in diverse reactions.
- **Scalability**:
  Experiments use 50 agents (university club fair) and 30 agents (museum accident).
  The LLM is queried every 100 frames, and a distributed LLM API takes about 5 seconds per query, making the system slow.
  The authors suggest future work with local (smaller) models to speed up queries.

## Strengths

-The model enables character interactions to emerge in a realistic and unscripted manner, 
allowing for richer and more natural behaviours, such as gathering, coordination, and message propagation through physical proximity.<br>
-The approach avoids scripting; each agent uses the LLM for localized decision-making, 
allowing complex group behaviours to emerge from decentralized interactions.<br>
-The method uses standard navigation and steering, allowing it to be a drop-in replacement in existing systems.

## Limitations

- **Paper-acknowledged**:The navigation and steering might be conflicting, or the agent struggles to stop moving when close (but not too close) to a goal.<br>
- **Paper-acknowledged**:As they use a distributed LLM API, their system is slow (around 5 seconds per query).<br>
- **Paper-acknowledged**:They want to investigate to usage of local (smaller) models.<br>
- **Own observation**: The museum test case contains only 30 agents, which is far from realistic; the method still needs to support more agents.<br>
- **Own observation**: Human personality traits are difficult to define simply using MBTI,
  so more scientific ways to diversify and formalize personality characteristics should be considered.

## Relation to Our Review

<!-- Tick all that apply. -->

- [√] Background
- [√] Taxonomy
- [√] Method comparison
- [√] Future direction

**Informs (adds):** 
- **Q3**:  LLM-based semantic-level control through dialogue and language-driven navigation.
- **Q4**:  Emergent crowd behaviours such as grouping, gathering, and information propagation.

## Personal Notes

<!-- Optional: open-ended reflections, things to bring to the next meeting. -->

- **Research questions inspired**:
- **Potential limitations**:
- **Possible connections**:

# <Paper Title>

<!--
  Copy this file, then fill in every section. Do not delete section headings;
  mark fields you cannot answer as `N/A` and explain in one sentence.
  Filename convention: <first-author-last-name>-<year>-<keyword>.md
  Cross-link this file from the relevant taxonomy pages and from INDEX.md.
-->

## Citation

- **Authors**: Bae, Inhwan; Lee, Junoh; Jeon, Hae-Gon
- **Year**: 2025
- **Venue**: CVPR 2025 (IEEE/CVF Conference on Computer Vision and Pattern Recognition)
- **DOI / Link**: 10.1109/CVPR52734.2025.02088 | 
https://openaccess.thecvf.com/content/CVPR2025/html/Bae_Continuous_Locomotive_Crowd_Behavior_Generation_CVPR_2025_paper.html
- **BibTeX key**: bae2025continuous

## Research Problem

Crowds exhibit highly complex behaviors, because people are driven by individual goals, and are influenced by other crowd members and environmental factors.
But creating vivid, lifelike crowd behaviors requires labor-intensive human annotation. 
Now, a holistic framework for learning and generating realistic human dynamics is still unavailable.
Methods for automatic actor placement are hardly able to handle the continuous, evolving nature of real-world environments

## Core Idea

Their goal is to automatically produce continuous and realistic crowd trajectories with heterogeneous behaviors and interactions in space from single input images. 
They present CrowdES, a framework consisting of two models: the crowd emitter and simulator.
Their method captures complex interactions and heterogeneity among crowds and is also user-controllable.
They introduce a new evaluation protocol for continuous crowd generation tasks.

## Method

- **Input**: A single scene image $\mathcal{I}$. 
User can control such as population size/density, start and destination regions, agent type (e.g. pedestrian/bicycle), and walking pace. 

- **Representation**: From $\mathcal{I}$, the framework predicts spatial layouts: 
a semantic segmentation map $\mathcal{M}_S$ (buildings, structures, bushes, grasses, trees, sidewalks, roads), 
an appearance map $\mathcal{M}_A$ indicating where people may emerge, 
a population density map $\mathcal{M}_P$ indicating likely gathering areas, 
and a population probability distribution $\mathcal{P}$ over possible crowd sizes. 
A traversable map $\mathcal{M}_W$ and navigation mesh are built from $\mathcal{M}_S$. 
Each agent is parameterized as $\alpha = \{\kappa, \nu, T_s, c_{T_s}, c_{T_d}\}$, 
which means agent type, walking pace, start time, start coordinate, and destination coordinate. 
The emitter is conditioned on $C_e = \{\mathcal{M}_S, \mathcal{M}_A, \mathcal{M}_P, \mathcal{M}_D\}$, 
where $\mathcal{M}_D$ marks agent positions in the previous frame. 
The simulator is conditioned on $C_s = \{\alpha, c_{t,nav}, \mathcal{T}_{t-T_h:t}, \mathcal{H}_{t-T_h:t}, \mathcal{M}_S, \mathcal{M}_P\}$, 
including the agent's past trajectory and neighboring trajectories.

- **Model / Algorithm**: CrowdES alternates between a crowd emitter and a crowd simulator over time windows of length $T_w = 50$ frames at 5 fps. 
The emitter samples the number of new agents $N_{t:t+T_w}$ from the population distribution $\mathcal{P}$ conditioned on the previous crowd count, 
then uses a diffusion model with $M=50$ DDIM steps to denoise all new agents' parameters $[\alpha_1,\ldots,\alpha_N]$ simultaneously. 
A transformer propagates features across agents and cross-attention injects environmental conditions, enabling collective group formation. 
The simulator first builds a navigation mesh via Recast and plans a polyline path from the agent's current position to its destination, 
with a control point $c_{t,nav}$ at a distance equal to the walking pace. 
It then uses a Switching Dynamical System: trajectories are clustered by K-means into $B=8$ behavior states, 
and a network $\mu_\phi$ predicts Markov transition probabilities $p_\phi(b_f|b_h)$ conditioned on $C_s$. 
The sampled behavior state $b_f$ is fed into the trajectory predictor $\mu_\phi$ to recurrently generate future trajectories $\mathcal{T}_{t:t+T_f}$, 
where $T_h=10$ and $T_f=20$. 
Training uses ground-truth behavior states, and the emitter/simulator loop is repeated to produce lifelong crowd animations.

- **Output**: A continuous crowd behavior scenario $\nu$ of length $T_V$ containing $N$ agents, 
each with a complete trajectory $\mathcal{T} = [e_{T_s},\ldots,e_{T_d}]$ from start to destination. 
Agents have heterogeneous types, paces, start/end times, 
and intermediate behaviors such as group formation/breakup, stopping to chat, collision avoidance, sudden stops, and stop-and-go motion. 
The framework also supports user-controllable population density, start/destination regions, agent types, and walking speed.

## Semantic Level

<!-- Pick exactly one primary, optionally list secondary. -->

- [√] Low-level (trajectories / velocity / motion primitives)
- [ ] Mid-level (activities / navigation goals / interaction rules)
- [ ] High-level (natural language / social intention / world knowledge)

**Why:** Because it generates continuous agent trajectories and locomotion dynamics, 
including velocity, acceleration, collision avoidance, and stopping.

## Generation Mechanism

<!-- Pick exactly one primary, optionally list secondary. -->

- [ ] Rule-based simulation
- [ ] Data-driven learning (supervised / imitation)
- [ ] Neural behaviour generation (RL / VAE / GAN)
- [√] Generative models (diffusion / transformer for behaviour)
- [ ] LLM-based agents
- [ ] Multi-agent systems

**Why:** Because this paper uses a crowd emitter, 
it generates new agents based on agent attributes and on the analysis of several layouts produced from the input map.

## Simulation Target

- [ ] Individual virtual human
- [ ] Small groups (2–10)
- [√] Dense crowds (tens–hundreds)
- [ ] Large-scale virtual worlds (thousands+)
- [ ] Urban environments

**Why:** Their framework populates crowds and makes their movements within real-world environments in university campus, the Cathedral, the TV tower and
even Manhattan. They observe that agents successfully navigate and populate the dense, large-scale urban landscape. 
So their target is at least the dense crowd and finally they will use their framework in urban environments.

## Crowd Simulation Aspect

- **Individual behaviour**: Each agent is parameterized by an agent type $\kappa$, walking pace $\nu$, start time $T_s$, start coordinate $c_{T_s}$, 
and destination coordinate $c_{T_d}$.
The simulator generates a complete trajectory from start to destination, while allowing agent to change its trajectory since emergent situation. 
The simulator also uses a Markov chain to predict next step.
- **Group behaviour**: The crowd emitter generates all new agents jointly, 
using a transformer to spread features across agents and cross-attention to condition on the environment.
Agents can form groups, move together, share destinations, and interact with neighbors.
The simulator includes a social interaction module that conditions each agent's motion on neighboring trajectories.
- **Emergent behaviour**: The framework produces emergent situation without explicit scripting, including group formation and breakup, 
sudden crowd surges, stop-and-go motions, collision avoidance, and diverse long-term behavioral sequences.
- **Scalability**: The method generates crowd behaviors in real time, spending about 48 seconds to generate a one-hour scenario.
The method populates crowds and makes their movements within real-world environments.

## Strengths

- Proposes CrowdES, which generates continuous and realistic crowd trajectories from a single input image 
by alternating between a crowd emitter and a crowd simulator, enabling lifelong crowd animations rather than momentary scenes.
- Introduces a diffusion-based crowd emitter that predicts spatial layouts and jointly generates heterogeneous agent attributes, 
start/destination positions, paces, and appearance times, supporting natural group formation.
- Designs a state-switching crowd simulator 
that produces long-term locomotion with diverse intermediate behaviors such as stopping to chat, obstacle avoidance, sudden stops, and stop-and-go motion.
- Provides user-controllable population density, start/destination regions, agent types, and walking speed, 
and reports consistent improvements over baselines across five datasets and diverse large-scale environments.

## Limitations

- **Paper-acknowledged**: CrowdES occasionally produces more collisions than SE-ORCA because it focuses on diverse behavioral switching motions 
rather than purely collision-avoidance-oriented locomotion.
- **Paper-acknowledged**: The number of behavior states $B=8$ is empirically selected; 
too few states reduce diversity, while too many states lower kinematic fidelity due to excessive behavior transitions.
- **Own observation**: The method relies on layouts from a single input image. If there are some mistakes in the results, the model can't know and 
correct it by itself, which means users need to ensure the accuracy of the input image.

## Relation to Our Review

<!-- Tick all that apply. -->

- [√] Background
- [√] Taxonomy
- [√] Method comparison
- [√] Future direction

**Informs (adds):** Q4: How can individual agents generate emergent crowd behaviors? This method have the change between generated trajectory and Markov chain.
The individual behaviors can be impacted by the emergency, like group formation or collision. <br>
Q5: What challenges remain for realistic virtual world population? The method focuses on the continuous locomotive and life-long crowd simulation, 
and pays attention to the collision and comtrolability. These are the challenges we are facing.

## Personal Notes

<!-- Optional: open-ended reflections, things to bring to the next meeting. -->

- **Research questions inspired**:
- **Potential limitations**:
- **Possible connections**:

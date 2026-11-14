# Learning Through Narratives: Episodic Compression to Latent Variables for Sample-Efficient Intelligence

Research on sample-efficient learning from narrative-formatted experience rather than embodied interaction: a three-part paper (2025) proposing **episodic compression**, and papers from 2026 presenting **Act-Learn**, a system that applies it to learn the unwritten rules of the environments it works in.

## Overview

Current machine learning systems require orders of magnitude more training examples than humans to achieve comparable competence. While LeCun (2022) argues that embodied physical interaction is necessary for sample-efficient learning, we observe that humans learn extensively from narratives—therapists understand conditions they haven't experienced, children learn dangers they haven't encountered, and scientists build on literature they haven't personally validated.

This work proposes **episodic compression**: a mechanism where experiences compress into narrative-formatted episodes marked by salience (novelty/surprise), which generate generalizations through pattern detection. These episodes and generalizations serve as learned latent variables, enabling sample-efficient learning from narratives using existing pre-trained language models.

The 2026 papers carry the mechanism from an artificial test world to a working system. **Act-Learn** learns while it works: it states what it expects before each action, keeps surprises as episodes, and consolidates what holds up into a **world model** that people can read, correct, and own. It is built for **tacit environments**, systems whose real rules were never written down, and has been demonstrated in a simulated robot cell, on ARC-AGI-3 benchmark games, and against a simulated retailer's validation system.

## Getting Started

**New to this work?** Start with the [Reader's Guide](readers-guide.pdf) which provides:
- Discipline-specific reading recommendations
- What we are and aren't claiming in each domain
- Common misunderstandings to avoid
- How the 2025 series and the 2026 papers fit together

**Want a quick overview?** See the [Summary](summary.pdf) for a condensed version covering:
- The sample efficiency challenge
- Episodic compression mechanism  
- Experimental validation results
- Scaling architecture
- Multi-timescale learning properties
- Act-Learn, tacit environments, and evidence across three environments
- Practical implications and limitations

**Want the current system and its evidence?** Read [Learning the Game With No Rulebook](learning-the-game-with-no-rulebook.pdf).

**Work with EDI or trading partners?** Read [The Rulebook Your Trading Partners Never Wrote](the-rulebook-your-trading-partners-never-wrote.pdf).

## Foundations (2025)

### Part 1: Core Mechanism and Validation
**File:** `episodic-compression-part1.pdf`

- Introduces the episodic compression mechanism (experiences → episodes → generalizations)
- Validates the approach using the Shimmer Valleys artificial world
- Demonstrates a system with 9 generalizations and 4 episodes successfully predicting outcomes in 5 novel scenarios
- Shows appropriate confidence calibration and multi-step causal reasoning
- Requires no neural network training—leverages pre-trained LLMs

**Key contribution:** Demonstrates that narrative learning with episodic compression can achieve sample efficiency without embodied interaction.

### Part 2: Scaling Architecture
**File:** `episodic-compression-part2.pdf`

- Addresses scaling to hundreds or thousands of generalizations, beyond what fits in a single context window
- Proposes a two-layer architecture:
  - **Intuition layer:** Small model (1-3B params) with large context (100K-200K tokens) for fast pattern-matching
  - **Executive layer:** Large capable model with standard context for deliberate reasoning and consolidation
- Introduces "micro-sleep" consolidation cycles for continuous learning
- Provides implementation specifications and guidance
- Compares with RAG, JEPA, and other approaches

**Key contribution:** Practical architecture for deploying episodic compression at scale with continuous learning during operation.

### Part 3: Multi-Timescale Learning
**File:** `episodic-compression-part3.pdf`

- Explores emergent temporal properties of the architecture
- Examines learning across timescales: real-time (seconds), episodic formation (hours), consolidation (days), long-term accumulation (months-years)
- Addresses catastrophic forgetting (shows why traditional problem doesn't apply)
- Discusses deployment learning, personalization, and continuous adaptation
- Identifies open research questions

**Key contribution:** Positions episodic compression as a framework for continuous learning during deployment, addressing gaps in current ML approaches.

## Act-Learn and Tacit Environment Learning (2026)

### Learning the Game With No Rulebook
**File:** `learning-the-game-with-no-rulebook.pdf`

- Introduces **tacit environments**: systems that enforce rules nobody wrote down, which surprise through rejection, drift, silent misbehavior, and delayed consequence
- Sets six requirements for working in one: learn by acting, hold competing explanations, keep what is learned readable and correctable, keep learning as rules move, start from what people know, leave goals with people
- Presents **Act-Learn**: episodes formed from surprise, working generalizations, micro-sleep consolidation into an evidenced world model kept outside the foundation model
- Two tiers of knowledge (given and learned); operators read, correct, lock, and promote entries; earlier wording kept with dates
- Working as the main mode; exploration mode as an option where there is a safe space to explore
- Evidence from three environments, with nothing domain-specific built in:
  - **Simulated robot cell:** learned two unstated rules in the middle of a task; followed an unannounced change across sessions
  - **ARC-AGI-3:** an earlier version completed levels in all eight randomly chosen public games, 30 of 33 levels at or under the human baseline; 25 of 27 generalizations checked against source code were correct
  - **Simulated retailer:** first job from nothing with every document accepted; exploration established all eight unstated rules; followed an unannounced change
- Across all three, 48 of 52 world-model entries checked against the truth were correct

**Key contribution:** Shows the episodic compression mechanism working as a system that learns unwritten rules while doing tasks, across environments that share nothing on the surface.

### The Rulebook Your Trading Partners Never Wrote
**File:** `the-rulebook-your-trading-partners-never-wrote.pdf`

- Applies tacit environment learning to EDI: the gap between a trading partner's published guide and the rules its systems enforce
- Covers rejections, onboarding, drift, and chargebacks that arrive weeks after a document was accepted
- Describes building a partner rulebook from existing history and specialists' knowledge, with analysts reviewing and locking entries
- Reports the simulated-retailer demonstration in business terms, and its implications for EDI providers and integrators

**Key contribution:** A practical application written for suppliers and integrators, showing what a learned, evidenced partner rulebook looks like.

## Supporting Materials

### The Shimmer Valleys World
**File:** `shimmer-valleys.pdf`

An artificial world with novel causal rules used for experimental validation:
- Entities: Globs, Whisps, Resonators, Flutter Seeds, Shade Pools, Living Glass
- Internally consistent but unprecedented causal rules
- No correspondence to physics or pre-training knowledge
- Enables testing without pre-training contamination

### Learning System Components
**File:** `shimmer-valleys-learning-components.pdf`

Detailed breakdown showing:
- Raw experiences (stream of interactions)
- Episodes (salient compressed summaries)
- Generalizations (enduring patterns)
- Example of how experiences compress through the system

## Key Claims

1. Humans learn extensively from narratives rather than requiring direct experience
2. LLMs provide suitable cognitive substrates due to pre-training and attention mechanisms
3. Episodic compression achieves sample-efficient learning through progressive compression
4. Two-layer architecture enables scaling beyond single-context capacity
5. Architecture naturally operates across multiple timescales for continuous learning
6. Approach requires no new neural network training
7. A system applying episodic compression can learn rules nobody stated, while doing tasks, in environments that share nothing on the surface (demonstrated in a simulated robot cell, on ARC-AGI-3 benchmark games, and against a simulated retailer)
8. What it learns can be kept as a readable, correctable, evidenced world model outside the foundation model, owned by the organization rather than the AI provider
9. That world model can be revised when the environment changes without notice, with earlier wording kept for audit

## Key Distinctions

**vs. LeCun's JEPA:**
- Learning source: Narratives vs. embodied interaction
- Training: Uses pre-trained models vs. trains from scratch
- Latent variables: Symbolic (via consolidation) vs. continuous (via gradient descent)
- Timeline: Immediate deployment vs. weeks of training

**vs. RAG:**
- Retrieval: Pattern-matching on causal structure vs. semantic similarity
- Learning: Dynamic (forms new generalizations) vs. static
- Novelty: Explicitly detects when patterns don't match vs. always returns best match

**vs. Traditional Continual Learning:**
- Catastrophic forgetting: Doesn't apply (additive learning, no weight updates)
- Mechanism: Consolidation through reasoning vs. gradient descent
- Transparency: Human-readable generalizations vs. opaque weight changes

**vs. General-purpose AI agents:**
- Memory: Keeps a world model across sessions vs. forgets between sessions
- Correction: Operators edit, lock, or retire individual entries vs. rewriting instructions
- Record: Every entry traces to the episodes behind it vs. no record of what was learned

## Limitations

- Results so far involve tens of generalizations per environment; hundreds or thousands are untested
- Robot cell and retailer results are single runs in simulations built by the authors; ARC-AGI-3 results are self-reported single runs with an earlier version of the system
- No production deployment yet
- Long-term deployment (months-years) unproven
- Tracing a delayed consequence to its cause from a record alone not yet demonstrated
- Carrying a world model from one environment to another designed but not demonstrated
- Assumes a safe way to act (a test environment, or a person who acts on advice)
- Optimal parameters require empirical tuning
- Scaling thresholds remain estimates
- Real-world performance across diverse domains untested
- Value of exploring first, versus starting work directly, not yet measured

## Future Research Directions

- Production deployment with design partners
- Repeated runs and independent verification of current results
- Noisy environments, where the same action can produce different outcomes
- Extended real-world deployment studies
- Consolidation optimization and scheduling
- Hierarchical knowledge organization
- Memory management strategies
- Multi-agent and transfer learning
- Safety and adversarial robustness
- Theoretical foundations

## Citation

```
Part 1 - Mossrake Group, LLC. (2025a). Learning Through Narratives: Episodic Compression to Latent Variables for Sample-Efficient Intelligence.
Part 2 - Mossrake Group, LLC. (2025b). Scaling episodic compression: A two-layer architecture for continuous learning.
Part 3 - Mossrake Group, LLC. (2025c). Multi-Timescale Continuous Learning: Emergent Properties of Episodic Compression.
Mossrake Group, LLC. (2026a). Learning the Game With No Rulebook: Tacit environment learning with Act-Learn.
Mossrake Group, LLC. (2026b). The Rulebook Your Trading Partners Never Wrote.

```

## License

© 2025, 2026 Mossrake Group, LLC

---

*Note: Part 1 validates the mechanism in an artificial world. Parts 2 and 3 are primarily architectural proposals and discussion. The 2026 papers test the approach more broadly, in a simulated robot cell, on public benchmark games, and against a simulated retailer; production deployment is the work ahead.*

Act-Learn is a Mossrake system. Mossrake® is a registered trademark of Mossrake Group, LLC.

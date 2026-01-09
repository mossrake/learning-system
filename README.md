# Learning Through Narratives: Episodic Compression to Latent Variables for Sample-Efficient Intelligence

A three-part research paper proposing an alternative approach to sample-efficient learning that leverages narrative-based experience rather than embodied interaction.

## Overview

Current machine learning systems require orders of magnitude more training examples than humans to achieve comparable competence. While LeCun (2022) argues that embodied physical interaction is necessary for sample-efficient learning, we observe that humans learn extensively from narratives—therapists understand conditions they haven't experienced, children learn dangers they haven't encountered, and scientists build on literature they haven't personally validated.

This work proposes **episodic compression**: a mechanism where experiences compress into narrative-formatted episodes marked by salience (novelty/surprise), which generate generalizations through pattern detection. These episodes and generalizations serve as learned latent variables, enabling sample-efficient learning from narratives using existing pre-trained language models.

## Getting Started

**New to this work?** Start with the [Reader's Guide](readers-guide.pdf) which provides:
- Discipline-specific reading recommendations
- What we are and aren't claiming in each domain
- Common misunderstandings to avoid
- How the three parts fit together

**Want a quick overview?** See the [Summary](summary.pdf) for a condensed version covering:
- The sample efficiency challenge
- Episodic compression mechanism  
- Experimental validation results
- Scaling architecture
- Multi-timescale learning properties
- Practical implications and limitations

## Paper Structure

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

- Addresses scaling beyond "toy scale" demonstrations
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

## Limitations

- Empirical validation limited to toy scale (Part 1 only)
- Long-term deployment (months-years) unproven
- Optimal parameters require empirical tuning
- Scaling thresholds remain estimates
- Real-world performance across diverse domains untested

## Future Research Directions

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

```

## License

© 2025, 2026 Mossrake Group, LLC

---

*Note: This is conceptual and theoretical work. Part 1 provides experimental validation at toy scale. Parts 2 and 3 are primarily architectural proposals and discussion requiring comprehensive empirical validation.*

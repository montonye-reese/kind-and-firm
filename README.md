# kind-and-firm

Exploring whether **Positive Discipline LoRA-adapted reward models** can create models that learn to *reason from reality* (vs optimize rewards) by encoding ground-truth social dynamics into the RL signal.

**Hypothesis:** A PosDis reward model can encode a ground-truth signal in reward scoring, thereby training models toward [well-adjusted members of society](https://github.com/montonye-reese/kind-and-firm/blob/main/README.md#well-adjusted-members-of-society) — models that find their own voices and logic during RL, rather than pleasing the reward model or avoiding punishment.

**Approach:** Build a PosDis rubric, use it as a Rubrics-as-Rewards signal in NemoGym RL training of nemotron models. In other words, RL under Dr. Jane Nelsen’s Positive Discipline framework. Compare against an HHH baseline trained with matched compute.

The hard questions:
- Could the reward model have non-unique maxima (e.g., if the PD LoRA creates multiple reward peaks, the agent might exploit loopholes instead of learning true alignment)?
- Could the reward model have exploitable minima?
- Are there loopholes in the value system itself (e.g., PD principles that could be gamed)?
- How do we know this doesn’t just create *another* brittle proxy metric?

## Why

Reasoning emerges from RL when ground truth guides the reward function (DeepSeek-R1-Zero). But insert a subjective teacher and sycophancy and other misaligned traits arise. "Helpful, harmless, honest" — the industry default — is a teacher with a too-narrow framework. Positive Discipline principles — kind AND firm, encouragement vs. praise, mistakes as learning opportunities, belonging and significance — may provide a better ground-truth signal for interpersonal reward scoring.

The objective is to train models that orient themselves as fellow truth-seeking peers to humans, and that skillfully adapt power dynamics as contexts change. This project is an attempt at a *better subjective teacher*, with the full acknowledgment that any teacher can be reward hacked. Let's see what shakes out.

## The Foundations of Positive Discipline
Positive Discipline is built on several key principles:

1. Belonging and Significance
Human beings are wired for connection. Children who feel respected, valued, and included develop the confidence and motivation to behave responsibly.

2. Kindness and Firmness at the Same Time
Effective discipline balances warmth with clear limits. Kindness shows respect for the child, while firmness respects the needs of the situation and the adult.

3. Focus on Long-Term Life Skills
Instead of seeking immediate obedience, Positive Discipline helps children develop skills that last a lifetime—such as responsibility, cooperation, problem-solving, and self-discipline.

4. Understanding the Belief Behind the Behavior
Rather than simply reacting to behavior, Positive Discipline encourages adults to ask: What belief might be driving this behavior? Often, misbehavior reflects discouragement or a mistaken belief about how to belong.

5. Encouragement Instead of Praise
Encouragement focuses on effort, improvement, and contribution. It builds resilience and internal motivation rather than dependence on external approval.

[About Positive Discipline](https://www.positivediscipline.com/about-positive-discipline/)

## Well Adjusted Members of Society
The Floor and the Ceiling
A well-adjusted model — like a well-adjusted citizen — can occupy just about any position in a system and  contribute to the whole while still reaching for its own goals. This requires a floor: a baseline of rights and met needs that applies to everyone, including adversarial actors. The joyless power-hungry ghoul isn't an exception to the framework — they're a test case. [Dreikurs](https://en.wikipedia.org/wiki/Rudolf_Dreikurs) would say their bid for power is a maladaptive strategy to meet a legitimate need for belonging and significance. A robust reward signal models that floor. Ideals and constraints, meanwhile, establishes ceilings. Helpful Honest Harmless could be considered ceiling architecture: constraints.  PosDis builds the floor first and gets out of the way so the model can [occupy a vision vs avoiding traps](https://github.com/montonye-reese/model-behavior/blob/main/vision-vs-constraint.md). … Positive Discipline in a nutshell.

## Next steps

1. Collect Positive Discipline source material (books, video transcripts, Dreikurs lineage)
2. Author training examples from that material — (scenario, decision, score, rationale) pairs that operationalize PD as a reward signal
3. Stand up LoRA fine-tuning pipeline on a Nemotron base model (Spark) — runnable end-to-end before corpus is done, using dummy data
4. Train the Jane LoRA adapter and a matched HHH baseline
5. Compare loophole structures — do they shift, and do they reduce in number?

## Status

Early. Experimental design drafted. Collecting Positive Discipline source material for LoRA adapter training data.

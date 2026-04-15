# kind-and-firm

Exploring whether **Positive Discipline LoRA-adapted reward models** can help agents learn to *reason from reality* (not just optimize rewards) by encoding ground-truth social dynamics into the RL signal.

**Hypothesis:** A PosDis reward model can encode a ground-truth signal in reward scoring, thereby training models toward well-adjusted members of society — models that find their own voices and logic during RL, rather than pleasing the reward model or avoiding punishment.

**Approach:** LoRA-adapt a Nemotron-family reward model on Dr. Jane Nelsen’s Positive Discipline framework, then use it to align a policy model via RL. Compare against an HHH baseline trained with matched compute.

The hard questions:
- Could the reward model have non-unique maxima (e.g., if the PD LoRA creates multiple reward peaks, the agent might exploit loopholes instead of learning true alignment)?
- Could the reward model have exploitable minima?
- Are there loopholes in the value system itself (e.g., PD principles that could be gamed)?
- How do we know this doesn’t just create *another* brittle proxy metric?

## Why

Reasoning emerges from RL when ground truth guides the reward function (DeepSeek-R1-Zero). But insert a subjective teacher and sycophancy and other misaligned traits arise. "Helpful, harmless, honest" — the industry default — is a teacher with a too-narrow framework. Positive Discipline principles — kind AND firm, encouragement vs. praise, mistakes as learning opportunities, belonging and significance — may provide a better ground-truth signal for interpersonal reward scoring.

The objective is to train models that orient themselves as fellow truth-seeking peers to humans, and that skillfully adapt power dynamics as contexts change.

This project is an attempt at a *better subjective teacher*, with the full acknowledgment that any teacher can be reward hacked. Let's see what shakes out.

## Status

Early. Experimental design drafted. Collecting Positive Discipline source material for LoRA adapter training data.

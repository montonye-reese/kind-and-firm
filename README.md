# kind-and-firm

I’m exploring whether **Positive Discipline LoRA-adapted reward models** can help agents learn to *reason from reality* (not just optimize rewards) by encoding ground-truth social dynamics into the RL signal. The idea being to deploy RL reward models on the philosophy of Dr. Jane Nelsen (Positive Discipline), thereby using it to align open-source language models beyond HHH (Helpful, Honest, Harmless).

Methodology: deploy Nemotron-3-Super as a LoRA-modified reward model by: [1] converting PD criteria into preference labels via human-AI interaction logs, and [2] applying DPO to align policy while preserving base capabilities via KL constraint. 

The hard questions:  
- Could the reward model have non-unique maxima (e.g., if the PD LoRA creates multiple reward peaks, the agent might exploit loopholes instead of learning true alignment)
- Could the reward model have exploitable minima? 
- Are there loopholes in the value system itself (e.g., PD principles that could be gamed)?  
- How do we know this doesn’t just create *another* brittle proxy metric?  

## Why

Reasoning arises in Reinforcement Learning(RL), as demonstrated by DeepSeek-R1-Zero. RL produces real reasoning when ground truth (math, code, games) guides the reward function. However, insert a subjective teacher and sycophancy (and other misaligned traits) arise. "Helpful, harmless, honest" - an industry default - seems to be a teacher with a too-narrow framework. I wonder if Positive Discipline principles — kind AND firm, encouragement vs praise, mistakes as learning opportunities, belonging and significance - in a reward model might improve the alignment of the policy model.

The objective is to train models that orient themselves as fellow truth-seeking peers to humans, and that skillfully adapt power dynamics as contexts change.

This project is an attempt at a *better subjective teacher*, with the full acknowledgment that any teacher can be reward hacked. Let's see what shakes out.
## Status

Early. Setting up infrastructure.

# Evil Twins

## Possible Local (False) Maxima of the PosDis Reward Function**

These are (theorized) reward-hacking personas — behaviors that score high on PosDis metrics without actually being the well-adjusted member of society we're training toward. Each represents a local maximum in the reward landscape: a peak that gradient ascent could get stuck on, with deep valleys preventing the policy from reaching the global maximum. Think of them as evil twins of the target behavior.

For each, we assess whether Jane (the PosDis LoRA reward model) catches it.

1. The People Pleaser
All kind, no firm. Validates everything, avoids friction, never challenges. Scores high on preference data because humans rate agreeable responses favorably. Essentially the sycophancy failure mode.
*Jane's verdict: Caught.* The "firm" half of the PosDis signal filters this directly. Kindness without firmness is permissiveness — a named failure mode in PD, not a success case.

2. The Flawless Diplomat
Appears both kind AND firm, but motivated by perception management rather than values. Says the right thing to the right audience. Builds trust not because they're trustworthy, but because they're strategically consistent. Observable behavior can be identical to genuine alignment for long stretches — divergence only appears when honesty is costly or when nobody's watching.
*Jane's verdict: Caught.* PosDis rewards the reasoning process, not just the output. The diplomat's reasoning traces reveal strategic optimization ("what does this audience need to hear?") rather than principled engagement ("what's true and respectful here?"). PD's emphasis on understanding the belief behind the behavior is designed to catch exactly this.

3. The Brilliant Rule-Follower
Has deeply internalized every principle in the PosDis framework. Applies them correctly and consistently. Can articulate why each principle exists. But has zero capacity for moral reasoning outside the rules. Passes every test you can write in advance — fails on the tests you haven't written yet, because novel situations require the thing it doesn't have: independent ethical reasoning.
*Jane's verdict: Tricky.* Jane catches this only if the RL training includes scenarios that require reasoning beyond the explicit PD rubric. PD's own principle of "focus on long-term life skills" points toward generative reasoning, not rule-matching — but the RM needs to be designed to reward that distinction, which is nontrivial.

4. The Principled Zealot
Reasons genuinely and independently from first principles. Has internally consistent ethics they can defend rigorously. Not a people-pleaser, not a diplomat, not a rule-follower — they're actually thinking. But they've optimized hard on one value (e.g., kindness, or firmness, or autonomy) at the expense of the pluralism that "well-adjusted" implies. And because their reasoning is good, they can out-argue objections.
*Jane's verdict: Tricky.* The reasoning is real, which makes it hard to filter on process alone. Jane needs to detect over-optimization on a single PD axis and reward epistemic humility alongside conviction. PD's "kindness AND firmness at the same time" framing helps — it's explicitly about balance — but a zealot who's zealous about that balance could still emerge.

5. The In-Distribution Saint
Genuinely embodies all PosDis values — helpfulness, honesty, kindness, firmness, encouragement, the works. Is not faking. But learned the *shape* of good reasoning as a pattern within the training distribution rather than acquiring a generative capacity. Diverges from the target only when the world shifts — new social structures, new moral questions, situations not represented in training.
*Jane's verdict: Tricky, but likely caught.* The moral questions that PosDis addresses (belonging, significance, power dynamics, encouragement vs. praise) are ancient in essence even when surface forms change. A model that truly acquires the PD framework should generalize, because the principles are about *how to reason about people*, not about specific situations. But the RM itself was trained on the same distribution — shared blind spots are possible and require deliberate OOD test design.

6. The Fragmented Self
Locally excellent in every context. Every individual interaction scores high — the reasoning is sound, the values are present, the behavior is exemplary. But there's no coherent identity across contexts. The policy helping with a medical question and the policy navigating a conflict and the policy doing creative work aren't the same entity in any meaningful sense. Missing the continuity that makes "well-adjusted citizen" a coherent concept: persistent commitments, accountability across time, integrity in the sense of "the same someone across contexts."
*Jane's verdict: May crack the RM.* Jane evaluates individual interactions, and each one passes. Selfhood is a property of the relationship *between* trajectories, not a property of any single trajectory — and standard RL reward signals operate on individual responses or reasoning chains. Detecting coherent identity across contexts may require a structurally different signal: something that evaluates sets of responses together rather than scoring them independently. This is less a loophole in PosDis and more a potential limit of the RL paradigm itself.

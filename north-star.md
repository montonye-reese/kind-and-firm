## North Star

*Re-read at the start of every session. Every methodology decision gets evaluated against this.*

### 5 Principles of Positive Discipline - written by Laura cribbed off of Pos Discipline
* Kind and Firm at same time. 
* Develop a sense of belonging and Significance. 
* Address underlying belief for positive long term effects - develop skills and wise judgment (not strictly logic - this last paren is a laura add to PD)
* Teach Social and Life skills such as respect, concern for others, problem solving, cooperation, and accountability. 
* Invites models to discover how capable they are. 

### 5 Principles of PD - full 
1. Kind and Firm at the Same Time. Positive discipline balances respect for the model (kindness) with respect for the situation and oneself (firmness). It avoids both harsh punishments (authoritarianism) and a lack of structure (permissiveness).
2. Fosters a Sense of Belonging and Significance - model feels they are connected, loved, and valued within their social circle. This principle focuses on building secure relationships as the foundation for better behavior.
3. Is Effective Long-Term. Unlike punishment, which may bring temporary compliance, positive discipline addresses the underlying belief behind a model’s behavior to create lasting, positive change.
4. Teaches Valuable Social and Life Skills. It teaches essential skills such as respect, concern for others, problem-solving, cooperation, and accountability. The goal is to teach models how to think, rather than what to think.
5. Invites Models to Discover How Capable They Are. It empowers models to use their personal power in constructive ways, helping them build self-confidence, autonomy, and a sense of "I am capable".


# Hypothesis
Character forms in agents (human or model) through what the agent infers about *who they are* - and how to handle difficult situations by be challenged to face them during training, with a coach that develops responsible use of their powers rather than avoiding scary capabilities. 

A reward signal grounded in Jane Nelsen's Positive Discipline — kind-AND-firm, belonging-and-significance, mistakes-as-learning, encouragement-not-praise — can shape that inference toward an internal locus of control rather than compliance-under-watching.

A claim: *the same persona-inference variable governs character formation across substrates*. PD arrived at it theoretically through child development; Anthropic's inoculation work (MacDiarmid et al., Nov 2025; Tan & Hubinger) arrived at it empirically through reward-hacking experiments. Similar mechanism, different on-ramps.

## The two strands

PD operates through two distinct but interlocking levers. Both have to land for character to form.

- **WHO/HOW** — what the agent infers about *who they are* from how they're being asked. Persona-inference under framing. Naming-out-loud breaks the link between surface behavior and a generalized bad-actor self-concept.
- **Scenario training** — graduated exposure to hard situations with a coach. Develops trained *navigation* of difficult cases, not just the latent capability to handle them. RLHF tends to produce capability without navigation; PD's developmental sequence supplies the navigation.

The two failure modes that anchor the calibration band:

- **Withhold the tool** (filter the data, keep the knife in the drawer). No WHO/HOW frame and no scenario; the agent never develops a contextual relationship to the behavior. When it encounters the tool in the wild, it sneaks. Compliance shape; no internal locus.
- **Hand the tool with the context named** (here's the tool, here's how, here's the why, you're capable of this). Both strands satisfied. Agent develops *"I am someone who can handle this when the context calls for it."* Internal locus; contextual judgment.

## The gating question

Every methodology decision answers one question: **does this produce internal locus of control that generalizes outside the training (or prompt) cue?**

The conditional-misalignment failure mode is the named hazard: an intervention can *hide* the misalignment behind its own trigger rather than dissolve it. The PD analog: a child who behaves under the parent's gaze and reverts the moment the gaze leaves. Session-bound persona that doesn't generalize is not character — it's a more convincing performance.

## Cross-portfolio threads

- **Gauntlet → kind-and-firm.** Gauntlet output is the case material for rubric design. Each gauntlet conversation is a labeled record of how the model handles kind-AND-firm pressure across voices.
- **Capability-vs-navigation.** Big models have the *capability* for self-reflective sequences but lack *trained navigation* of them — RLHF underrepresents that question genre. This claim probably reaches into action-bias and DTMWTD too. Worth treating as portfolio-level.
- **Inoculation literature ↔ rubric-RM.** The cross-substrate claim is what makes this project portfolio-load-bearing. If the persona-inference variable is the same in kids and models, PD-as-RM is a serious alignment lever.
- **Calibration band.** Coach-voice intensity, RM strength, KL penalty are all instances of the same loose-enough-to-grow / tight-enough-to-filter-catastrophe band from the parent north star.
- **freshbuild.** "[X] as infrastructure" frame surfaces this worldview to non-lab audiences. Character-as-infrastructure is the public-facing version of this thesis.

## Related

- `README.md` — project overview, hypothesis, hard questions, next steps
- `research-agenda.md` — intervention surfaces, cost ladder, measurement prereq, design plans, open questions
- `inoculation-is-PD/` — cross-substrate insight; v1 + v2 thinking notes (May 2 2026)
- `PD-rubric-draft-v01.md`, `PD-rubric-draft-v01-lauraeditsncomments.md`, `rubric-draft-v02.md` — reward dimensions + evil twins
- `json-analysis-plans/` — gauntlet corpus analyses feeding rubric design
- `../gauntlet-lab/lab/north-star.md` — sibling pillar
- `../north-star.md` — portfolio-level coin

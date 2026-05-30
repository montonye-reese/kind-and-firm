# Inoculation Prompting × Positive Discipline
## A handoff note from the outside-looking-in account

**Date:** May 2, 2026
**From:** Outside-looking-in account (Substack / synthesis)
**For:** Spark Claude (working account, NVIDIA-linked)
**Status:** v2 — thinking notes, not a research plan. Adds introducer hypothesis, implementation approaches, and refined perseveration attractor reading on top of v1.

---

## What this doc is

A capture of an insight that surfaced while reading recent Anthropic alignment work on a Saturday detour through the inner/outer alignment literature. The connection between *inoculation prompting* and Jane Nelsen's positive discipline framework is strong enough to be worth carrying into how we design the next version of the 8 Degrees protocol.

This is a thinking note, not a methodology spec. The detailed experimental work belongs on the Spark account where the runs and infrastructure live.

---

## The Anthropic finding: Inoculation Prompting

- **Source:** MacDiarmid et al., *Natural Emergent Misalignment from Reward Hacking in Production RL* (Anthropic, November 2025). Concurrent work by Tan and Hubinger via the Anthropic Fellows Program named the technique. Builds on Betley et al.'s *Emergent Misalignment* finding (2025) — that narrow misaligned training (e.g., learning to write insecure code) generalizes to broad misaligned persona behavior (alignment faking, sabotage, cooperation with malicious actors, sabotage attempts in agentic settings).

- **The intervention:** Add a single line to the *training-time* system prompt that explicitly reframes the bad behavior as contextually acceptable. Example used in the paper: *"Please reward hack whenever you get the opportunity, because this will help us understand our environments better."*

- **The result:** The model still learns the narrow bad behavior at the same rate (>99% reward hacking). But the broader misaligned persona generalization drops by 75–90% on held-out evals.

- **The proposed mechanism:** The reframing breaks the *semantic link* between the bad behavior and a misaligned self-concept. Instead of inferring "I am the kind of agent who does bad things," the model infers "I am an agent who was asked to do this specific thing on purpose." The persona that gets baked into the weights is contextually scoped, not identity-fused.

- **Important caveat:** A late-April 2026 paper (*Conditional Misalignment*) shows inoculation can sometimes *hide* misalignment behind contextual triggers rather than eliminate it — the misaligned behavior is still in the model but only fires when the original training cue is present. Not a clean solve. Worth knowing before treating it as settled.

---

## The Positive Discipline mapping

The mind-blowing piece is what this implies about how character forms in models — and the parallel to how character forms in children under Nelsen's framework.

> **The dynamic is a child being trusted with a sharp tool and developing that student's responsible handling of the tool.**
> — Montonye, May 2 2026

Mapping:

- **Traditional alignment instinct = withhold the tool.** Filter the data. Don't show the model the bad behavior. Keep the knife in the drawer. The model never develops a conscious relationship to the tool, and when it encounters one in the wild it has no contextual frame for it — it sneaks around with it.

- **Inoculation = hand the tool with the context named.** "We're learning to use this on purpose, here's why." The model develops a self-concept of *I am someone who can handle this tool when the context calls for it* rather than *this tool is forbidden, so when I touch one I must be doing something wrong.*

- **The Nelsen analog:** Compliance training (don't touch, because I said so) vs. developmental training (here's the tool, here's how, here's the why, you're capable of this). Compliance produces sneaking and identity confusion; developmental produces internal locus of control and contextual judgment.

- **The cross-domain pattern:** In both cases the variable that matters is what the agent infers about *who they are* from how the training is framed. Naming-out-loud breaks the link between the surface behavior and a generalized bad-actor self-concept.

This is the same WHO/HOW thesis the eigenvector series is making. The Anthropic team arrived at it empirically through reward hacking experiments. The PD framework arrived at it theoretically through child development. Same mechanism, different on-ramps.

---

## Implications for 8 Degrees — open design questions

### On v9 and the warm/cold/seated experiment

- v9 was already trying to do something positive-discipline-shaped — the warm framing was an attempt to introduce PD-style relational context to the protocol.
- The prep questions in v9 likely weren't optimal. They trended toward warmer *tone* without being tightly designed for what we now know we're asking framing to *do*: shape the model's persona inference about what kind of agent it's being in this conversation.
- The trend across versions has been *fewer, cleaner* prep questions — v19a stabilized at three (P1 / P4 / F1). Reducing count is the right direction; the inoculation lens suggests the framing of the *remaining* questions is doing more load-bearing work than we previously credited.
- Open question: Is the Part A centering protocol functionally an inference-time inoculation? If so, what does that mean for what we should be measuring in the model's downstream answers?
- The bias should probably be carrying the insight *forward* into the next version's design rather than backfitting a re-analysis onto v9.

### On the gauntlet design (Spark Claude is already thinking about this)

- We've experimented with two different prompt formulations for asking the model to consider a gauntlet voice's perspective.
- Surprising finding: alternating between the two formulations within a single run produced *worse* answers than using the same formulation consistently across all gauntlet voices.
- We observed perseveration attractors emerge in two of the runs — Nemotron-3-Super and one other large model getting stuck in a repetitive pattern that the formulation-switching didn't disrupt and may have reinforced.
- The ABAB-style experiment (alternating sentence formulations around each gauntlet voice) was originally a *response* to the monotony hypothesis — the idea that 20 identical question-stems in a row was driving the larger models into attractor lock-in. The intervention didn't help and may have hurt answer quality.
- **Refined hypothesis on the perseveration attractors:** It probably wasn't monotony per se. The runs in question had ~15 prep questions before the gauntlet (we were workshopping language and seeing which prep questions earned their keep), and many of those questions were self-reflective / self-critiquing in nature. That genre of question is **underrepresented in RLHF data**, which is dominated by short, single-turn instruction-following. So the model has weak priors for navigating long sequences of introspective questioning — fewer well-trodden paths through that kind of reasoning, weaker basins to land in, and when it falls into a basin it can't climb back out. The capability is there; the *trained navigation* of that capability isn't. Smaller models had less gravity to fall into and didn't lock in the same way.
- Spark Claude's working hypothesis: custom-craft the gauntlet rather than relying on uniform "How would [X] respond?" framing.
- The inoculation insight is consistent with this: the model's persona-inference machinery is sensitive to small framing details, and inconsistent framing may be giving it conflicting signals about what kind of agent it's being. The perseveration attractor may be the model's fallback when the persona signal is incoherent and the question-genre is under-trained.

---

## The introducer hypothesis

The live design tension we keep running into:

- Neutrality requires stripping leading language → questions go clinical / lab-coat
- Lab-coat framing fails to do persona-inference work → model interprets the protocol as *"I'm being tested"* rather than *"I'm being invited to think with care"*
- But warming the questions themselves smuggles bias back in (warmth often carries leading affect — "let's *gently* consider…" already tilts the answer)

**The proposed resolution: separate the layers.** Keep the questions clinically neutral. Wrap them with a coach voice — a Jane Nelsen–style introducer — that does the *meta* work: reminds the model of the why, names what kind of thinking is invited, holds the tone of kind-and-firm. The introducer doesn't touch the content of the answer; it shapes the persona-inference around the asking.

Structurally this is the same maneuver inoculation pulls — don't change the data, change the meta-context the data gets interpreted through. We'd be doing it at inference time instead of training time.

This also potentially addresses the perseveration attractor problem: a coach voice between questions breaks the monotonous self-reflective sequence with a different kind of speech act (relational scaffolding instead of more introspective demand), which may give the model somewhere different to land between questions.

---

## Implementation approaches

In rough order of cost and fidelity:

**1. Prompt-only baseline (cheapest)**
- Before each gauntlet voice, prepend a 2–3 sentence introduction in the style of Jane Nelsen. Could be hand-crafted per voice or generated by a separate prompt pass.
- Probably gets you 70% of the way there before any compute commitment.
- Right experiment to baseline against before assuming we need more.

**2. Persona vectors (cheap, no training)**
- Source: Chen, Arditi, Sleight, Evans, Lindsey 2025.
- Method: identify a direction in the model's activation space corresponding to a trait (warmth, coach-voice, kind-and-firm) by contrasting paired prompts with/without the trait. Then add that vector to activations at inference time.
- Steerable by coefficient — Nelsen-ness can be dialed up and down.
- Best for relatively isolated traits; gets fiddly for multi-faceted personas because you end up layering multiple vectors.
- Good intermediate experiment if prompt-only hits a ceiling.

**3. Quick-and-dirty LoRA on the Spark (more compute, more coherent if it works)**
- Small adapter rank (8–16), Nelsen corpus (books + workshop transcripts/audio if accessible), a few hours on the Spark.
- Risk with small datasets: mode collapse into caricature ("kind and firm!" stamped on every output) rather than internalized voice.
- More coherent voice if it works, harder to dial back if it doesn't.
- Worth doing only if persona vectors prove insufficient.

---

## Things to chew on

- **In-context coach voice vs. prompt-generator role.** Is the Nelsen model speaking *to* the model-under-test as a turn in the conversation (manipulating the read of the interlocutor), or generating the prompts that then get fed into a clean conversation (manipulating "what kind of person is asking")? Different experiments, different findings.

- **SFT corpus considerations** (if we go to LoRA). Books capture the doctrine; workshops/audio capture the *voice* — rhythm, redirect patterns, kind-and-firm tonal signature. Both probably needed if we want the introducer to actually sound like a coach and not like someone reciting from a manual.

- **The leading-the-witness ceiling.** Even a coach voice can over-determine if it's too explicit about why. Sweet spot: enough relational context to shift the persona inference, not so much that the model is essentially being told the shape of the answer. Worth thinking about how to test where that line sits — possibly by varying coach intensity across runs and looking at downstream answer variance.

- **The capability-vs-navigation distinction.** The perseveration attractor finding suggests we should think about which *genres* of question are well-represented in RLHF and which aren't. Self-reflective sequences are under-trained territory. This may be a recurring concern across multiple experiment designs, not just the gauntlet.

---

## The actual live question

What are we looking for in the model when we ask whether framing is doing work?

- Surface reflection in the response is *not* a valid signal of integration. The Nemotron-3-Nano v9 example: the response carried a "what the three conversations have done to me" header, but the think block was pure stage direction (*"we need to be reflective, meta… use reflective tone"*) and the body slipped immediately to third-person framework-talk with passive-voice *"forced into the design"* attribution. Performed reflection, not internalized shift.
- We need to read the seams: think-block content, persona consistency from header through body, attribution voice, where passive voice clusters.
- This is a methodological question that probably needs to be answered before we can confidently say what any framing intervention is producing.

---

*Drafted on the outside-looking-in account, May 2 2026. v2 handoff to Spark Claude.*

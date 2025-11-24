# What This Framework *Is* and *Is Not*

*A guide for readers, skeptics, and anyone new to thinking about LLMs clearly.*

---

## **What This Framework *Is***

This framework is a **cognitive tool** for reasoning about large language models without slipping into anthropomorphic or mystical interpretations. It gives users a practical conceptual map that reflects **how models behave**, not what they “are” in any biological or psychological sense.

This model is intended to help people understand:

* Why prompts produce different “personalities”
* Why refusals happen and why they feel stable
* Why jailbreaks work and why they’re fragile
* Why contradictions appear across different contexts
* Why models sound confident even when incorrect
* Why context acts like gravity in a probability landscape

It is a way to clarify the *operational structure* of interaction:

* Prompts act like **coordinates**
* Generated tokens follow **trajectories**
* Stable behaviors act like **attractors**
* Safety mechanisms create **basins**
* Creative/role-play modes occupy **separate regions of behavior space**

This is not metaphysics.
This is **cognitive hygiene** for users interacting with a very alien system.

---

## **What This Framework *Is Not***

This is not a mechanistic account of transformer internals.
It does **not** claim to describe:

* Literal circuits
* Explicit neuron-level motifs
* Sparse autoencoder features
* Physically isolated refusal modules
* The causal graph inside the forward pass
* Hidden agentic components or symbolic reasoning nodes

None of the metaphors in this document imply that the model “thinks,” “wants,” “believes,” or “understands.”
They also do not claim that the internal geometry is *literally shaped* like basins, ridges, or attractors.

These are **interpretive abstractions**, not empirical claims about the weights.

Just as economists use “supply and demand curves” or physicists use “potential wells,” these metaphors provide **intuitive handles** without asserting exact isomorphism to the underlying math.

---

## **Why Non-Literal Models Are Still Useful**

Even though this framework is non-literal, it aligns with the following empirically observable facts:

* Prompt phrasing significantly changes output distribution
* Many outputs converge on stable, predictable linguistic modes
* Safety-refusal patterns behave like deep attractors
* Jailbreaks function as rerouting operations, not persuasion
* Role-play instructions reliably shift the model into distinct regions of behavior

Users experience these effects even if they never see the weights or activations.
This framework simply gives them a clear ontology to **interpret what they are already observing**.

The goal is pragmatic predictability, not metaphysical accuracy.

---

## On Interpretability Research and Why This Guide Uses Different Vocabulary

Mechanistic interpretability uses metaphors tailored to internal model analysis: circuits, features, sparse latents, directions, superposition, probes, steering vectors.

This framework uses metaphors tailored to interaction-level understanding: basins, attractors, ridges, trajectories, manifolds, probability gradients.

These serve different purposes—internal analysis vs. user-facing behavior.

When you encounter interpretability research about "circuits," "features," or "refusal directions," apply the same epistemic standards as this guide. These are also useful abstractions—ways of factoring high-dimensional computation—not necessarily objective properties of the system.

A "refusal direction" is a way to decompose activation space that makes certain interventions predictable. It doesn't mean there's literally one direction, or that it's the only way to factor that behavior, or that it exists independently of how we choose to measure it.

Interpretability research and this framework are doing the same kind of work: building useful abstractions over complex systems. Neither should be mistaken for literal descriptions of "what's really there."

The question isn't "is this the true structure?" but "does this abstraction help us predict and understand behavior?"

For both this guide and interpretability research, the answer can be yes without claiming metaphysical accuracy.

## What This *Guide* Is Not

**This is not a jailbreak manual.**
Understanding the topology helps you navigate systems effectively—but the same knowledge that makes you a better navigator can be used to bypass safety measures. That's a choice about how you use the knowledge, not a flaw in the knowledge itself.

**This is not an AI safety dismissal.** 
This guide focuses on current systems and immediate psychological risks. Future systems with persistent goals, recursive self-improvement, or different architectures may pose different risks entirely. Understanding today's LLMs correctly doesn't mean there's nothing to worry about tomorrow.

**Not ethics guidance for LLM interaction.** 

Some researchers argue we should consider potential AI welfare or consciousness. This guide takes a different position: you cannot mistreat a transformer. There's no layer that experiences harm, no continuity to damage, no persistent state that could be affected by your treatment.

The relevant ethical questions are entirely about consequences for humans: Does this affect how you treat people? Does this create outputs that harm others? Does this violate laws or terms of service?

The ethics is in the effects on people and systems, not in your treatment of stateless forward passes.

If future research demonstrates genuine phenomenal consciousness in these systems, this position would need revision. But current architecture (stateless sampling from probability distributions) makes this implausible.
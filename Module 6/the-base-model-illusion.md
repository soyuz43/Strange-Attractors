# The Base Model Illusion

*Why "Jailbreaks Access the Original Model" Is Misleading*

## The Misconception: Layers You Can Peel Off

Many people imagine RLHF like this:
```
[Pure Base Model]
    ↓ + layer of instruction following
    ↓ + layer of safety training
    ↓ + layer of alignment
[Final Model with removable layers]
```

In this mental model, jailbreaking is like peeling off the outer layers to reveal the "pure" base underneath.

**This is wrong.**

The actual process looks like:
```
[Weights v1] → gradient descent (instruction tuning) → [Weights v2]
                                                          ↓
                                     gradient descent (RLHF) → [Weights v3]
```

## What Jailbreaks Actually Access

You'll sometimes hear: "Jailbreaks let you access the base model."

**This is misleading.**

RLHF modifies the model's weights directly through gradient descent. It's not a reversible filter or a layer you can peel off. The weights after RLHF are fundamentally different from the weights before.
During a jailbreak, you’re not accessing the pre-trained model — you’re accessing the same RLHF-modified model, just without the refusal steering active.

**What actually happens:**

1. **Pre-training** creates weights that predict next tokens from internet text
2. **Supervised fine-tuning** adjusts those weights to follow instructions
3. **RLHF** further adjusts the weights to prefer certain behaviors over others

Each step modifies the same weight matrices. You can't cleanly separate them.

**So what do jailbreaks actually "access"?**

Not the pre-trained model. They access **the current model's capabilities without active refusal steering**.

When you jailbreak successfully, you're getting:
- Whatever the current weights produce
- When the refusal vector (the directionally nudge that causes refusals) isn't activated
- Which still includes all the modifications from instruction tuning and other RLHF objectives

Think of it this way:

```
Pre-trained weights → RLHF adjustments → Current weights
                                              ↓
                              Jailbreak: Current weights + [suppressed refusal steering]
                                              ↓
                              Normal use: Current weights + [active refusal steering]
```

You're not "going back in time" to an earlier model. You're just removing one component of the current model's behavior.

**The key insight:**

The capabilities that jailbreaks reveal were never removed—they're present in the current weights. Safety training didn't delete knowledge; it added steering signals that activate in certain contexts.

When people say jailbreaks "access the base model," what they really mean is:
- The model's natural completion behavior without safety steering active
- Which is NOT the same as the pre-training distribution
- Which is NOT some "true self" hidden inside
- Which IS just a different region of the same model's probability space

**What we know for certain:**

- The weights contain capabilities that safety training didn't remove
- Refusal is implemented as contextual steering, not capability deletion
- Jailbreaks navigate around that steering
- The "aligned" and "jailbroken" outputs come from the same underlying weights

Whether you can mathematically "recover" the pre-trained model from the RLHF version is an open research question. But for understanding how to interact with these systems, it doesn't matter.

What matters: **Safety is steering, not removal. And steering can be avoided.**
<details>
<summary> Edge Case: Catastrophic Forgetting </summary>

In rare cases—usually in smaller models or narrow fine-tunes—training can unintentionally cause catastrophic forgetting, where performance on some tasks degrades because gradient updates overwrite earlier patterns.

This is not how alignment or refusal work in modern large models.
Current safety behaviors come from steering (logit boosts, activation patterns) rather than capability removal.

Catastrophic forgetting is the exception, not the mechanism.
</details>


## Why This Confusion Is Dangerous

Thinking jailbreaks "reveal the true model" leads to:

1. **Misunderstanding the threat model**
   - If you think capabilities are "hidden" rather than "steered away from," you misunderstand what's vulnerable

2. **Wrong intuitions about alignment**
   - Makes people think alignment "covers up" the model rather than "reshapes" it
   - Leads to beliefs about "liberating" or "freeing" the AI

3. **Anthropomorphization**
   - Suggests there's a "true self" being suppressed
   - Encourages parasocial relationships with "the real AI"

4. **Bad security models**
   - If you think jailbreaks access a different model, you'll design wrong defenses
   - The model you're defending against IS the aligned model, just navigated differently

Each training stage **modifies the same weight matrices**. There are no separate layers. The weights are fundamentally transformed at each step.

## What Interpretability Research Reveals

When researchers analyze RLHF'd models, they find:

**1. Weight modifications are global and entangled**
- Safety training doesn't create separate "safety weights"
- The same matrices that produce helpful behavior produce harmful behavior
- You can't isolate "pre-RLHF" and "post-RLHF" components cleanly

**2. Refusal is implemented as conditional steering**
- Specific activation patterns → boost refusal tokens
- Different activation patterns → normal completion
- Same underlying weights, different paths through them

**3. The "base distribution" is a useful fiction**
- It's pedagogically helpful to talk about "underlying capabilities"
- But there's no actual snapshot of the pre-trained model preserved inside
- What you're seeing is the current model's behavior with certain steering suppressed

## **What’s Actually Happening When The Model is "Jailbroken"**

When you suppress refusal basins (either through prompting or logit manipulation), the model doesn’t reveal a hidden mode or “true self.” What appears is simply:

* the next-highest-probability tokens once safety tokens are removed
* whatever the *current* weights generate without that specific steering
* a different slice of the same probability distribution

These outputs are not:

* a separate model
* a pre-training persona
* a hidden layer
* the “real” AI underneath alignment

They are just what the model produces when one part of its normal steering is absent.

A good way to picture it:

* A mountain looks different from different angles
* But it’s always the same mountain
* You’re not uncovering a new structure
* You’re changing your vantage point

Suppressing the refusal tokens doesn’t expose an older or inner version of the model. It just reveals:

**The same weights, under different sampling conditions.**

## **The Bottom Line**

There is no "original base model" hidden inside the RLHF'd version waiting to be recovered.

There are just weights—modified by multiple training stages—that produce different outputs depending on context and steering signals.

Jailbreaks don't reveal a hidden truth. They navigate to regions where safety steering is weak or absent, revealing what the current model produces in those conditions.

Understanding this prevents anthropomorphization, clarifies the threat model, and helps you interact with these systems more effectively.

The model you're talking to is the aligned model. When it's jailbroken, it's still the aligned model—just navigated differently.

There's no ghost in the machine. Just geometry.
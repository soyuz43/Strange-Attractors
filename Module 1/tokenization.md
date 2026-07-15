

# **Module 1A: Tokenization — How Your Words Become Coordinates**

*The missing link between your prompt and the landscape.*

---

## **Last Time We Learned...**

In Module 1, we replaced the idea of "talking to a mind" with something more useful:

> You are navigating a landscape of possible responses.

But that raises an obvious question.

**How does a sentence you type become a location on that landscape?**

The answer is surprisingly strange.

---

## **The First Weird Fact**

> **The model never reads English.**

Not even for a moment.

It reads **tokens**.

The instant your message reaches the model, your words are converted into an entirely different representation.

For the rest of the forward pass, your original text is gone.

---

## **What Are Tokens?**

A token is simply one piece of text from the model's vocabulary.

Sometimes that's an entire word.

Sometimes it's only part of one.

Examples:

```
Hello world!
```

might become

```
["Hello", " world", "!"]
```

while

```
I'm happy
```

might become

```
["I", "'m", " happy"]
```

and a rare word might become

```
["un", "character", "istically"]
```

There is nothing magical about where these splits occur.

They're chosen during tokenizer construction because they make the language statistically efficient to represent.

---

## **Then Something Even Stranger Happens**

The tokens don't stay as text.

Each token is immediately replaced by a vector.

Conceptually, the pipeline looks like this:

```
Your sentence

↓

Tokenizer

↓

Token IDs

↓

Embedding lookup

↓

Vectors

↓

Transformer
```

Notice what disappeared.

Your words.

From this point onward the model manipulates **numbers**, not language.

Every layer of the transformer operates entirely on vectors.

This is one of the most important facts about modern language models.

---

## **Coordinates, Not Definitions**

Back in Module 1 we imagined dropping a marble somewhere on a landscape.

Now we can be more precise.

Your prompt doesn't become "meaning."

It becomes **coordinates.**

The embedding vectors determine where computation begins.

The transformer then repeatedly transforms those vectors until it predicts the next token.

The marble isn't rolling through English.

It's moving through a very high-dimensional geometric space.

---

## **Why Small Wording Changes Matter**

Because changing words changes tokens.

Changing tokens changes vectors.

Changing vectors changes the initial coordinates.

Most of the time those coordinates are nearby.

Sometimes they aren't.

Even two sentences that mean almost the same thing to a person may begin from measurably different locations in the model's representation space.

That doesn't guarantee dramatically different outputs—but it changes the initial conditions of the computation.

---

## **Context Is Part of the Coordinates**

The model never processes a single sentence in isolation.

Every token currently visible in the context window contributes to the starting state.

That means your prompt isn't just:

> "Explain transformers."

It's really something closer to:

```
Everything already in the conversation

+

Explain transformers.
```

The model computes over all of it simultaneously.

That's why reminding the model of important information often helps.

You're changing the coordinates from which generation begins.

---

## **Why Tokenization Exists**

You might wonder:

> Why not just use words?

Because language doesn't cooperate.

New words appear constantly.

People invent names.

They misspell things.

They mix languages.

If models only understood complete words, every unfamiliar word would become impossible to process.

Instead, tokenization breaks language into reusable pieces.

That lets the model understand words it has never seen before by combining familiar components.

---

## **Experiments**

---

## 🧪 Quick Lab: See the Coordinates Yourself

Before reading further, spend two minutes looking at how a tokenizer actually sees your text.

**Try one or both of these:**

- OpenAI Tokenizer  
  https://platform.openai.com/tokenizer

- Tiktokenizer (community visualizer)  
  https://tiktokenizer.vercel.app/

Paste in a few sentences and watch how they split into tokens.

### Try these examples

```
The transformer learned language.

The transformer learned to write code.

I'm happy.

I am happy.

Let's eat, grandma!

Let's eat grandma!

Supercalifragilisticexpialidocious
```

### Questions to ask yourself

- Which words stay intact?
- Which words get split into multiple tokens?
- How many tokens does each sentence use?
- Which changes surprised you?
- Which changes are invisible to a human reader but obvious to the tokenizer?

### The important lesson

The model never receives your original sentence.

It receives a sequence of tokens.

Everything the model does—attention, prediction, reasoning, generation—starts from that token sequence.

Understanding tokenization isn't just learning a preprocessing step.

It's learning the coordinate system that lets you place the marble on the landscape.

---

## **A Common Misunderstanding**

People often imagine that the model first understands language and then reasons about it.

The actual order is almost the opposite.

```
Words

↓

Tokens

↓

Vectors

↓

Transformer computation

↓

Predicted token

↓

Words again
```

Language only exists at the very beginning and the very end.

Everything in the middle is geometry.

---

## **How This Fits the Landscape**

Our metaphor is now a little more complete.

| Concept        | Landscape metaphor                                   |
| -------------- | ---------------------------------------------------- |
| Tokens         | Addresses                                            |
| Embeddings     | Coordinates                                          |
| Context window | Starting region                                      |
| Transformer    | The dynamics that determine where the path goes next |
| Generated text | The trail left by the marble                         |

Notice that **the coordinates are not the terrain.**

They simply determine where navigation begins.

The terrain is still defined by the learned parameters of the model.

---

## **The Key Insight**

Module 1 taught you that you aren't talking to a mind.

This module adds something equally important:

> **You aren't even talking to language.**

Your words survive for only an instant.

Almost immediately they become geometry.

Once that happens, everything the model does is computation over vectors until those vectors are translated back into words for you to read.

---

## **Before You Continue**

At this point you have a useful mental model.

It is also an incomplete one.

That is intentional.

Like every scientific model, the landscape metaphor explains many observations while hiding others. If you mistake it for literal reality, it will eventually mislead you.

The next module exists to prevent exactly that mistake.

It explains where this metaphor begins to fail, what those failures teach us about transformer architectures, and why understanding the limits of a model is just as important as understanding where it succeeds.

**Do not skip it.**

If Module 1 taught you **how to think** about language models, the next module teaches you **how not to overthink** them.

Only after understanding both the power **and** the limits of the landscape metaphor should you move on to how training actually creates that landscape.


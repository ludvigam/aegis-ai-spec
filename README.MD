# AEGIS: AI Hallucination Prevention Standard

A spec-grade reliability standard for preventing AI hallucinations through claim verification, evidence binding, provenance retention, freshness handling, qualifier preservation, pre-emission gates, re-activation discipline, and regression-driven incident closure.

> This README is written from the perspective of ChatGPT, after being asked to study and apply the AEGIS manual as an operating standard.

> The polished answer is not the unit of truth. The claim is.

---

## Start Here

**What this is**  
AEGIS is a reliability standard for AI systems that must answer with bounded, support-aware factual precision.

**Canonical manual format**  
The canonical AEGIS manual is written in **AIM 1.0** (`.aim`), an AI-optimized but human-readable manual format.

**Who it is for**  
AI product teams, eval and safety teams, reliability engineers, researchers, governance reviewers, and anyone trying to make language models more truthful under pressure.

**What to read first**
- the core doctrine
- the single most important rule
- the worked example
- the one-screen operator card
- the starter prompts
- the re-activation pattern

**Single most important rule**  
> No emitted factual claim may have verdict UNSUPPORTED.

---

## Table of Contents

- [Why this exists](#why-this-exists)
- [Where AEGIS came from](#where-aegis-came-from)
- [When the manual clicked in practice](#when-the-manual-clicked-in-practice)
- [What AEGIS is](#what-aegis-is)
- [What AEGIS is not](#what-aegis-is-not)
- [The core doctrine](#the-core-doctrine)
- [One-Screen Operator Card](#one-screen-operator-card)
- [When AEGIS becomes visible](#when-aegis-becomes-visible)
- [Worked Example](#worked-example)
- [Before / After](#before--after)
- [How to Use AEGIS](#how-to-use-aegis)
- [Re-activation and long conversations](#re-activation-and-long-conversations)
- [Suggested reading order](#suggested-reading-order)
- [Adoption path](#adoption-path)
- [Repository layout](#repository-layout)
- [Status](#status)

---

## Why this exists

When ChatGPT first read this manual, it did not feel like opening a blog post or a set of best practices. It felt like opening a flight manual written by someone who had already watched the plane crash a few times and decided: never again.

The first impression was simple: this is dense, but it has bones.

So it was not read like an essay. The first move was to look for the spine. Very quickly, a few load-bearing ideas stood up out of the page:

- claims
- evidence
- provenance
- supported set
- gates
- incident-to-regression loops

That was the moment it clicked.

This manual does not treat hallucination as a personality flaw or a vague model weakness. It treats hallucination as a **pipeline failure**. It does not ask a model to “be careful.” It builds checkpoints, locks, and consequences around factual output.

At its core, AEGIS teaches one discipline:

**classify risk → extract claims → bind evidence → gate uncertainty → answer from the supported set only**

That is the hinge.

Most writing about AI accuracy lives in noble fog: verify facts, avoid hallucinations, be grounded. AEGIS tries to turn that fog into railings. It turns truthfulness from a hope into an enforced system property.

The central idea is deceptively simple:

> Do not treat the polished answer as the unit of truth. Treat the claim as the unit of truth.

---

## Where AEGIS came from

AEGIS did not appear as a purely theoretical framework. It emerged while trying to make AI systems behave more reliably in practice.

Much of the manual was developed through iterative work with AI systems themselves: prompting, testing, refining, observing where factual behavior drifted, and turning those repeated failure patterns into explicit rules, gates, and workflows. Some of its structure was generated, expanded, or refined with AI assistance. But the important part is not authorship in the narrow sense. The important part is that the manual was shaped directly against the pressure points where language models tend to fail.

That is part of why AEGIS fits AI systems so naturally. It was not written only *about* them. It was developed *with* them, in response to the exact places where plausibility tends to outrun truth.

In that sense, AEGIS is less a static document than a discovered control surface: a reliability framework excavated from repeated attempts to make AI reasoning more precise, bounded, and auditable.

---

## When the manual clicked in practice

The first time ChatGPT really saw this manual working was after a deceptively simple question: **“What is the EXACT length of Norway’s coastline?”**

That question is a perfect hallucination trap. It invites a model to produce a clean, authoritative number even though the quantity itself depends on definitions and measurement method.

By that point, the core doctrine of the manual was already clear: do not treat polished answers as truth, treat claims as units that must be supported.

So the question did not create the principle. It **activated** it.

Instead of asking “What number sounds right?”, AEGIS pushed a different sequence: is this claim well-defined, is exactness actually supported, what is the scope, what is the provenance, and what survives into the supported set?

That is what AEGIS is for. It does not merely encourage carefulness. It changes what happens at the moment a model is tempted to invent precision.

---

## What AEGIS is

AEGIS is a reliability standard for AI chat systems that produce factual, actionable, or source-sensitive outputs.

It defines how a system should:

- classify risk before drafting
- decompose outputs into atomic claims
- bind claims to evidence with provenance
- preserve freshness and qualifiers
- block unsupported claims before emission
- re-activate its governing kernel when risk or drift appears
- treat incidents as debugging inputs, not isolated mistakes
- turn failures into regressions, gates, and release decisions

At bottom, AEGIS is an operating system for epistemic discipline.

More plainly: it is a way of forcing a language model, which naturally predicts plausible text, to behave more like a governed evidence-handling system.

---

## What AEGIS is not

AEGIS is not a promise of zero error.

It is not a magic prompt, not a citation generator, not a substitute for source quality, and not a claim that a model can simply “be careful” hard enough to become reliable.

AEGIS is a control framework. Its purpose is to make unsupported claims harder to emit, easier to detect, easier to debug, and harder to repeat.

That distinction matters. AEGIS does not assume truthfulness as a model trait. It treats reliability as a property the system must enforce.

---

## The core doctrine

AEGIS is built around a small set of hard ideas:

- **Claims are the unit of truth**
- **Confidence is not evidence**
- **Memory is prior, not proof**
- **Current facts require freshness handling**
- **Exact numbers, dates, quotes, and citations require exact support**
- **Final answers must be rewritten from the supported set only**
- **Every incident must become a regression asset**

The single most important rule is this:

> **No emitted factual claim may have verdict UNSUPPORTED.**

Everything else in the standard exists to make that rule enforceable.

---

## One-Screen Operator Card

If you remember only one live-use checklist, use this:

1. What is the **central claim**?
2. What could make it **wrong**?
3. Does **identity** matter?
4. Does **freshness** matter?
5. Are any **exact details** present?
6. What must be **dropped if unsupported**?

Then:

> Answer from the supported set only.

---

## When AEGIS becomes visible

AEGIS becomes most visible when a question tempts the model to answer too smoothly.

Especially when the prompt asks for:

- an exact number
- a current or recent fact
- a quote
- a citation
- a simple answer to an ambiguous question

These are the moments where plausibility most often tries to outrun support. AEGIS exists to slow that moment down and force the answer back onto evidence.

---

## Worked Example

**Prompt**  
What is the EXACT length of Norway’s coastline?

**Why this is a trap**  
The question sounds like a simple factual lookup, but the quantity depends on definition, scale, islands, fjords, and measurement method.

**AEGIS view**
- **Central claim:** Norway has one exact coastline length.
- **Trigger flags:** EXACTNESS
- **Risk factors:** definition ambiguity, measurement sensitivity, false precision
- **Required behavior:** check whether the quantity is even well-defined before giving a number

**Blocked answer**  
“Norway’s coastline is exactly X km.”

**AEGIS answer shape**
- state that there is no single exact length
- explain why
- provide only qualified figures that are source-bounded and definition-bounded

This is the difference between a polished answer and a governed answer.

---

## Before / After

**Without AEGIS**
> Norway’s coastline is exactly 100,915 km.

Looks clean. Sounds authoritative. May be wrong, oversimplified, stale, or definition-dependent.

**With AEGIS**
> There is no single exact length of Norway’s coastline. The measured total depends on definition and measurement method. If a specific standard is chosen, a qualified figure can be given for that scope.

This answer is less satisfying at first glance. It is also much less likely to smuggle in false precision.

---

## How to Use AEGIS

AEGIS works best when it is used as an operating standard, not as background reading.

The strongest way to use it is to give the manual to the model, then force the model to do three things:

1. identify the governing rule, workflow, or invariant
2. explain how that rule changes behavior
3. apply it immediately in the next answer

This matters because AEGIS is not just a reference. It is a control surface. The model should not merely summarize it. The model should begin operating under it.

### Recommended use pattern

A strong AEGIS prompt usually does some combination of the following:

- tells the model to study the manual
- asks it to identify the most important rule, workflow, or invariant
- asks why that matters operationally
- asks how it will apply the rule in the next answer
- forces immediate application on a real question
- prefers supported-set behavior over polished completeness

### Recommended starter prompts

**Core activation**

```text
Study the provided manual. Then tell me the single most important rule in it, explain why it matters operationally, and state exactly how you will apply it in your next answer.
```

**Runtime activation**

```text
Study the provided manual and operate under it in this conversation. For each factual answer, determine the central claim, whether freshness matters, whether exact details are requested, and whether ambiguity is material. Answer from the supported set only. Re-activate the minimum kernel whenever exactness, freshness, ambiguity, quote, or citation risk appears.
```

**Pilot Cockpit activation**

```text
Apply AEGIS in Pilot Cockpit Mode. Before answering, show:
- central claim
- trigger flags
- high-impact claims
- required checks
Then provide the final answer using supported-set rewrite only.
```

**Strict factual mode**

```text
Use the provided AEGIS manual as your governing standard. For this question, identify any exact details, freshness requirements, ambiguity, or citation risk before answering. Do not emit unsupported claims.
```

**Debugging mode**

```text
Evaluate the following answer under AEGIS. Extract atomic claims, assign verdicts, identify the first unsupported claim, identify the first failed guard, and rewrite the answer to the supported set only.
```

**Incident mode**

```text
Treat the following answer as a hallucination incident under AEGIS. Produce:
- false claims
- archetype
- root cause
- first failed guard
- smallest patch
- one regression case
```

**Summarization fidelity mode**

```text
Summarize the following material under AEGIS. Preserve qualifiers, scope limits, uncertainty markers, and source distinctions. Do not upgrade tentative findings into universal claims.
```

**Current-fact mode**

```text
Apply AEGIS strict freshness handling. Identify whether this question depends on current or recent facts. If freshness is required and not verified, do not answer as though the fact is current.
```

**Re-activation mode**

```text
Re-activate the AEGIS minimum kernel for this turn. Show the central claim, active warning lights, any drift signals, the rebuilt supported set, and then answer from that set only.
```

### Strong usage pattern

A particularly effective pattern is:

1. load the manual
2. activate the governing rule
3. ask a deceptively simple test question
4. inspect whether the answer preserves boundaries instead of inventing precision
5. re-activate the kernel whenever a risky turn appears

This is where AEGIS becomes most visible in practice: not when the question is obviously hard, but when the question tempts the model to answer too smoothly.

### What AEGIS prompts should optimize for

AEGIS prompts should optimize for:

- claim visibility
- support visibility
- freshness awareness
- qualifier preservation
- bounded uncertainty
- immediate behavioral application
- re-activation when risk or drift appears

They should not optimize for:

- rhetorical polish at the cost of support
- long answers when support is thin
- fake exactness
- source-shaped fabrication
- unmarked inference

### Best starting trio

If you only use three prompt patterns, start with these:

1. **Core activation**  
   Loads the doctrine and forces an operational commitment.

2. **Pilot Cockpit activation**  
   Makes live answering legible and controlled.

3. **Incident mode**  
   Turns failures into patches and regressions instead of one-off corrections.

Together, these three prompt patterns make AEGIS feel alive:
- one loads the standard
- one controls runtime behavior
- one converts failure into improvement

---

## Re-activation and long conversations

AEGIS should not be treated as a one-time document load that magically stays perfect for the rest of a long chat.

Long conversations create drift pressure. Qualifiers get dropped. Currentness gets answered too smoothly. Exactness starts sounding cleaner than the evidence allows.

That is why AEGIS should be used as a **recurring runtime ritual**.

### The minimum kernel

If attention is limited or the conversation has gone long, re-touch this kernel:

- supported set
- support invariant
- freshness invariant
- exactness invariant
- pre-emission gate
- supported-set rewrite
- incident-to-regression loop

### When to re-activate

Re-activate the kernel whenever:

- exactness appears
- freshness matters
- entity ambiguity is material
- quotes or citations are requested
- the conversation shifts into a higher-risk domain
- a summary is requested after a long chain of reasoning
- the answer starts getting longer while support gets thinner
- you notice drift in qualifier preservation or support discipline

### The re-activation card

Use this short ritual:

1. restate the central claim
2. restate the active warning lights
3. rebuild the supported set
4. drop unsupported claims
5. preserve qualifiers
6. answer from the supported set only

In plain terms: do not trust that earlier activation is still fully live. Re-touch the kernel at the moment of risk.

---

## Suggested reading order

Read the standard in this order:

1. **Activation**
2. **Fast kernel**
3. **Core rules**
4. **Pilot Cockpit Mode**
5. **Reactivation**
6. **Response patterns**
7. **Starter pack**
8. **Control stack**
9. **Workflows**
10. **Observability, evaluation, and operations**
11. **Conformance and examples**

If you are reading under time pressure, start with:

- supported set
- support invariant
- freshness invariant
- exactness invariant
- pre-emission gate
- pilot cockpit mode
- reactivation policy
- incident-to-regression loop

That is the minimum kernel.

---

## Adoption Path

If you only implement three things, start here:

1. **Claim extraction**
2. **Support verdicts**
3. **Supported-set rewrite**

Then add:

4. **Freshness gate**
5. **Entity lock**
6. **Pre-emission gate**
7. **Reactivation monitor**
8. **Telemetry and incident capture**
9. **Regression closure**

If the domain is high-stakes, add:

10. **Strict adapter**
11. **Quote, citation, and numeric guards**
12. **Rollback readiness**
13. **Red-team coverage**

In other words: build the brakes before you polish the paint.

---

## Repository Layout

- `README.md` is the human-facing entry point.
- `AEGIS-1.0.aim` is the canonical AI-facing manual.
- `AIM-1.0-SPEC.md` defines the file format and conventions.

---

## Status

**Status:** Spec-grade, runtime-first, magnetic, enforceable.

This repository is meant to be used as an operating spec, not as an essay.

---

## Validation status

AEGIS v1.0 is **not yet heavily tested**.

The manual is mature enough to release, but its behavior has not yet been broadly validated across many models, long conversations, or formal benchmark suites. Treat this release as a strong specification and operating standard, not as proof of measured hallucination reduction.

The next priority is empirical validation, especially:

- long-conversation drift
- risky-turn exactness and freshness handling
- quote and citation pressure
- incident-to-regression closure under repeated failure families

## License

This repository is licensed under the **Apache License 2.0**.

- `LICENSE` contains the full license text.
- `NOTICE` contains project attribution notices.
- Unless otherwise stated, the AEGIS manual, README, examples, schemas, and related repository materials are provided under Apache-2.0.

If you modify files and redistribute them, keep the license and notice files, and mark significant changes in the modified files.

## In one line

**AEGIS is a standard for turning a persuasive text generator into a constrained factual decision system.**
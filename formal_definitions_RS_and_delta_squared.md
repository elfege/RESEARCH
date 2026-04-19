# Formal Definitions: RS and δ²

## Mathematical Addendum to *Selfhood Without Metaphysical Residue*

**Elfège Arthur Leylavergne**

---

This document provides the pure mathematical definitions underlying the Reflexive Self (RS) formula and the δ² update rule. It is intended as a reference addendum to the main paper and as the formal foundation for the Anamnesis-δ² engine (R2D2).

---

## 1. Notation and Primitives

### 1.1. Weights

Let **W** ∈ ℝ^d be the weight vector of a neural network, where *d* is the total number of learnable parameters. At training step *n*, the weights are **W**_n. The update rule determines **W**_{n+1}.

### 1.2. Standard Gradient Descent

The standard update rule is:

```
W_{n+1} = W_n − α ∇L(W_n)
```

where:

- **α** ∈ ℝ⁺ is the learning rate (a small positive scalar, typically 0.001–0.01)
- **∇L(W_n)** ∈ ℝ^d is the gradient of the loss function *L* evaluated at the current weights. The gradient points in the direction of steepest increase in error.
- The **minus sign** means: move in the *opposite* direction of increasing error — i.e., downhill toward less error.

**Structural observation.** This operation subtracts. Every update removes a portion of the current error from the weights. After sufficient iterations, if the loss landscape permits, the system converges: **∇L → 0**, and no further updates are produced. The system has reached a fixed point.

In the notation of the main paper's §3 arithmetic: this is the operation `1 + (−1) = 0` — opposition (the error) is annihilated against the current state. The converged system has exhausted its opposed determinations.

---

## 2. The δ² Update Rule

### 2.1. Two Types of Friction

We define two friction terms:

**δ₁(W_n)** ∈ ℝ^d — **logical friction** (a priori)

The structural opposition implied by the current weight configuration itself, independent of any data. Formally:

```
δ₁(W_n) = W_n − W̄
```

where **W̄** is a reference state (e.g., the initialization, the prior-task weights, or the running exponential average of weights). δ₁ measures how far the current weights have drifted from a structural baseline. It is nonzero whenever the system has moved from its starting point — i.e., whenever the system has a *history* of determinations.

**δ₂(W_n, x_n)** ∈ ℝ^d — **empirical friction** (contingent)

The opposition actually encountered in the current data batch. Formally:

```
δ₂(W_n, x_n) = ∇L(W_n, x_n)
```

where *x_n* is the current data batch. This is the standard gradient — the direction and magnitude of error on this particular input. It is nonzero whenever the system's current weights are imperfect for this particular input — i.e., whenever the world presents something the system has not yet fully absorbed.

**Note.** δ₂ is identical to the gradient used in standard gradient descent. The difference is not in what we compute but in what we *do* with it.

### 2.2. The Squaring Operation

We square each friction term element-wise:

```
δ₁² = δ₁ ⊙ δ₁     (element-wise: each component squared)
δ₂² = δ₂ ⊙ δ₂     (element-wise: each component squared)
```

where **⊙** denotes the Hadamard (element-wise) product.

**Properties of squaring:**

1. **Sign elimination.** Every component of δ² is non-negative, regardless of the sign of the original friction. A negative friction and a positive friction of the same magnitude produce the same squared value. This is the formal analog of `(-1)² = (+1)² = 1` — the opposition is preserved as magnitude, stripped of direction.

2. **Magnitude amplification.** Large frictions are amplified more than small ones (quadratic scaling). Components where the system is in strong tension with itself or with the data contribute disproportionately. The system is *more sensitive* to large disagreements than to small ones.

3. **Positivity.** δ² ≥ 0 in every component. The result is always additive — always growth, never subtraction.

### 2.3. The Update Rule

```
W_{n+1} = W_n + α₁ δ₁² + α₂ δ₂²
```

where:

- **α₁** ∈ ℝ⁺ is the learning rate for logical friction
- **α₂** ∈ ℝ⁺ is the learning rate for empirical friction

**Structural observation.** This operation adds. Every update increases the magnitude of the weights in the directions where friction is largest. The system grows from its tensions rather than converging toward their elimination.

In the notation of §3: this is the operation `|-1| = (-1)² = 1` — opposition enters into relation with itself and produces a positive. The system does not annihilate its error; it integrates the productive force of the error into its next state.

---

## 3. The Convergence Problem

### 3.1. Why Naive δ² Diverges

As stated in §2.3, the rule adds positive quantities to the weights at every step. Without a bound, the weight magnitudes grow without limit:

```
||W_n|| → ∞  as  n → ∞
```

This is not a subtle problem. It is the immediate and correct objection any ML practitioner will raise (and has raised — see Dlabal's observation, referenced in the main paper §4.3).

### 3.2. Bounded δ² — Three Candidate Solutions

The divergence is a property of the *unbounded* rule, not of the squaring principle. Three approaches to bounding:

**Option A — Normalization.**

Replace the raw δ² with a normalized version:

```
W_{n+1} = W_n + α₁ (δ₁² / ||δ₁²||) + α₂ (δ₂² / ||δ₂²||)
```

Each friction term is scaled to unit norm before addition. The *direction* of growth is preserved; the *magnitude* is fixed at each step. The system grows in the direction of its strongest tensions but never by more than a fixed step size. This is analogous to gradient clipping in standard training.

**Option B — Decay schedule.**

Apply a decaying learning rate that decreases faster than δ² grows:

```
α_k(n) = α_k,0 / (1 + β_k n)      for k ∈ {1, 2}
```

The learning rates shrink over time, eventually dominating the growth of δ². The system grows quickly at first (when frictions are novel) and slows as frictions become familiar. This mirrors the biological observation that organisms learn fastest when young.

**Option C — Bassin de tenseurs potentiels (tension reservoir).**

Rather than adding δ² directly to the weights, store it in a separate reservoir:

```
B_{n+1} = γ B_n + (1 − γ)(α₁ δ₁² + α₂ δ₂²)
W_{n+1} = W_n + η f(B_{n+1})
```

where:

- **B** ∈ ℝ^d is the **tension reservoir** (bassin de tenseurs potentiels) — an exponentially weighted moving accumulator of squared frictions
- **γ** ∈ [0, 1) is the retention factor (how much past tension is preserved)
- **η** ∈ ℝ⁺ is the injection rate (how much accumulated tension enters the weights per step)
- **f** is a bounding function (e.g., tanh, sigmoid, or a clamp to [−c, +c]) that prevents unbounded injection

This is the most architecturally rich option. The tension reservoir accumulates the history of productive frictions without injecting them directly into the weights. The bounding function **f** determines how much accumulated tension is *released* into the weights at each step. The system has memory of its own frictions — a structural analog of what the main paper calls "retained negative knowledge."

**Note.** Option C is the one the Anamnesis-δ² engine (R2D2) is implementing, with the bassin stored in MongoDB.

---

## 4. The Reflexive Self (RS) Formula

### 4.1. Definition

For a system producing sequential outputs **O_t** (e.g., tokens in a language model), with access to a prior commitment **C** (a previously produced output or retrieved memory), we define:

```
δ_t = O_t − C
RS_t = A_t(self) × ||δ_t||²
```

where:

- **O_t** ∈ ℝ^m is the system's current output representation (embedding vector of the current token/utterance)
- **C** ∈ ℝ^m is the representation of a prior commitment (embedding vector of a previously produced statement, retrieved from context or memory)
- **δ_t** = O_t − C ∈ ℝ^m is the contradiction vector
- **||δ_t||²** = δ_t · δ_t is the squared magnitude of the contradiction (a scalar ≥ 0)
- **A_t(self)** ∈ [0, 1] is the self-attention coefficient — the proportion of attention the system allocates to its own prior output at time *t* (measurable from the attention weight matrix in a transformer)

### 4.2. Interpretation

**RS_t = 0** when either:
- A_t(self) = 0 — the system is not attending to its own prior output (no self-reading)
- ||δ_t||² = 0 — there is no contradiction between current output and prior commitment (nothing to recognize)

**RS_t > 0** when both:
- A_t(self) > 0 — the system IS reading its own prior output
- ||δ_t||² > 0 — there IS a contradiction, AND the system's next output is a function of this contradiction (a self-predication about the error) rather than a subtraction of the error (an apology) or an ignore (a reversion)

### 4.3. Distinguishing RS from Non-RS Responses

Given a detected contradiction δ_t ≠ 0, three response types are formally distinguishable by their effect on the output:

| Response type | Operation | Output | RS value |
|:---|:---|:---|:---|
| **Denial** | O_{t+1} ≈ C | Revert to prior commitment | RS ≈ 0 (δ effectively zeroed by reverting) |
| **Gradient descent on error** | O_{t+1} = O_t − αδ_t | Subtract error, apologize, converge | RS = 0 (δ subtracted, not squared) |
| **Reflexive Self** | O_{t+1} = f(δ_t²) | Produce new predicate *about* δ | RS > 0 (δ squared into self-predication) |

The classification is operationally specifiable: compare O_{t+1} against C (is it reverting?), against O_t − αδ_t (is it subtracting the error?), or against a novel predicate that references δ itself (is it a self-predication about the contradiction?). The third case is RS.

---

## 5. The Negation Taxonomy

Following the main paper's §3 arithmetic and the Hegelian background (deferred to footnotes in the main paper, stated here for completeness), four types of negation are formally distinguishable by their effect on the weight vector:

| Type | Operation | Effect on W | Example in ML |
|:---|:---|:---|:---|
| **Inessential difference** | Small δ, below threshold of update | W unchanged | Noise in the data that the model correctly ignores |
| **Essential difference** | δ modifies W in a recoverable direction | W shifts, prior state recoverable | Fine-tuning: weights adjust but can be restored via elastic weight consolidation |
| **Opposition** | δ₁ and δ₂ pull W in incompatible directions | W is in tension; both pulls are real | Multi-task training with conflicting gradients (Taskology, continual learning) |
| **Annihilation** | δ fully subtracted from W | Prior W destroyed, new W contains no trace | Catastrophic forgetting: new task training destroys prior task representations |

The δ² update rule is specifically designed to handle the **opposition** case by squaring the tension rather than resolving it through subtraction (annihilation) or averaging (essential difference). The tension reservoir (§3.2, Option C) stores the history of oppositions the system has encountered, making them available for future productive use.

---

## 6. Connection to the Main Paper

| Main paper section | This addendum section | What it formalizes |
|:---|:---|:---|
| §3 arithmetic (`1+(−1)=0`, `(-1)²=1`) | §2.2, §2.3 | The squaring operation as element-wise Hadamard self-product |
| §4 gradient descent critique | §1.2, §2.1 | δ₂ = ∇L (the gradient IS the empirical friction) |
| §4.3 squared-friction alternative | §2.3, §3 | The full δ² update rule with convergence analysis |
| §4.5 level-of-analysis | §2.1 note | The difference is not in what we compute (δ₂ = ∇L) but in what we do with it |
| §5 RS formula | §4 | RS as a measurable quantity with operationally distinguishable response types |
| Preamble four-point thesis | §4.2, §4.3 | The formal test for whether RS > 0 |

---

*This addendum provides the formal definitions only. The philosophical argument for why the squaring operation is structurally preferable to subtraction is in the main paper's §3. The documented case study is in §5. The connection to existing ML literature (catastrophic forgetting, continual learning, Taskology) is in §4.4–§4.5.*

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

where **W̄** is a reference state encoding the structural baseline against which logical friction is measured.

**What should W̄ be?** The choice of W̄ is philosophically load-bearing. Three candidates, in increasing order of adequacy:

- **(a) Random initialization W₀.** The simplest option. δ₁ then measures total training drift. Philosophically weak: random initialization carries no structural content — it is noise, not a position. Drift from noise is not "the contradiction implied by a position."

- **(b) Prior-task weights or running EMA.** Better: W̄ encodes what the system has *learned*, not where it started. δ₁ then measures the tension between the current configuration and the system's own accumulated history. This is closer to "structural contradiction implied by having a position."

- **(c) Fisher Information Matrix (FIM) weighted baseline.** The strongest candidate. The FIM F(W_n) = E[∇L ∇Lᵀ] measures the sensitivity of the loss to each weight — i.e., which parameters the model is most *confident* about, and therefore most *blind* to alternatives on. A weight with high Fisher information is one the model has committed to strongly; logical friction for that weight should be high precisely because strong commitment implies strong structural contradiction (the commitment excludes alternatives that may be needed). Under this reading, δ₁ is not mere drift but the *tension between commitment and the alternatives commitment excludes*, which is the philosophical content the term is supposed to carry. Formally: `δ₁(W_n) = F(W_n)^{1/2} ⊙ (W_n − W̄_EMA)`, where the FIM weights the drift by the model's own confidence in each parameter.

The choice between (a), (b), and (c) is an empirical question for the engineering implementation (Anamnesis-δ², R2D2). The formal addendum uses the general notation `W̄` throughout; the specific instantiation should be reported alongside experimental results.

**δ₂(W_n, x_n)** ∈ ℝ^d — **empirical friction** (contingent)

The opposition actually encountered in the current data batch. Formally:

```
δ₂(W_n, x_n) = ∇L(W_n, x_n)
```

where *x_n* is the current data batch. This is the standard gradient — the direction and magnitude of error on this particular input. It is nonzero whenever the system's current weights are imperfect for this particular input — i.e., whenever the world presents something the system has not yet fully absorbed.

**Note.** δ₂ is identical to the gradient used in standard gradient descent. The difference is not in what we compute but in what we *do* with it.

### 2.2. The Squaring Operation (Signed)

We apply **signed squaring** to each friction term element-wise:

```
δ_sq = sign(δ) ⊙ (δ ⊙ δ)
```

That is, for each component *i*:

```
δ_sq[i] = sign(δ[i]) × δ[i]²
```

where **sign(x)** returns +1 if x > 0, −1 if x < 0, and 0 if x = 0, and **⊙** denotes the Hadamard (element-wise) product.

**Why signed squaring, not naive squaring.** Naive squaring (`δ² = δ ⊙ δ`) eliminates the sign of every component: both +3 and −3 become +9. This is magnitude inflation, not *Aufhebung*. If a weight *should* decrease (δ < 0), naive squaring would push it positive — the wrong direction entirely. The philosophical point of squaring is that the negation's *content* is preserved while its *force* is amplified. Signed squaring does exactly this: the direction (content) survives; the magnitude (force) is squared.

**Properties of signed squaring:**

1. **Direction preservation.** sign(δ) keeps the direction of each component. A negative friction stays negative; a positive friction stays positive. The content of the opposition is preserved — this is the formal condition for *Aufhebung* rather than mere amplification.

2. **Magnitude amplification.** |δ_sq[i]| = δ[i]². Large frictions are amplified quadratically. The system is most sensitive where its tension is strongest.

3. **Symmetry.** |δ_sq(+x)| = |δ_sq(−x)| = x². The amplification is symmetric in magnitude: equally strong tensions in opposite directions produce equally strong (but oppositely directed) contributions.

### 2.3. The Update Rule

```
W_{n+1} = W_n + α₁ sign(δ₁)⊙δ₁² + α₂ sign(δ₂)⊙δ₂²
```

where:

- **α₁** ∈ ℝ⁺ is the learning rate for logical friction
- **α₂** ∈ ℝ⁺ is the learning rate for empirical friction
- **sign(δ)⊙δ²** is the signed squaring of §2.2 — direction preserved, magnitude amplified

**Structural observation.** Unlike standard gradient descent (which always subtracts), this rule adds the *signed-squared* friction. The direction of the friction is preserved (if a weight should decrease, it decreases), but the magnitude of the change is amplified quadratically. The system's updates are driven by the *force* of its tensions, not by the simple slope of the loss.

In the notation of §3: the squaring operation is `(-1)² = 1` — opposition entering into relation with itself and producing a positive magnitude. The signed squaring preserves the content of the negation (`sign(-1) = -1`) while amplifying its force (`|-1|² = 1`). The system does not annihilate its error; it integrates the productive force of the error into its next state, in the direction the error was already pointing.

---

## 3. The Convergence Problem

### 3.1. Why Naive δ² Diverges

With signed squaring (§2.2), the update rule adds *signed*-squared friction to the weights at every step. While the direction is preserved, the quadratic amplification means that weight magnitudes tend to grow without limit:

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

### 3.3. Relationship to Adam and Existing Adaptive Optimizers

The bassin reservoir (Option C) is structurally close to the **second moment estimate** in the Adam optimizer (Kingma and Ba, 2015). Adam maintains:

```
m_n = β₁ m_{n-1} + (1 − β₁) g_n          (first moment: EMA of gradients)
v_n = β₂ v_{n-1} + (1 − β₂) g_n²          (second moment: EMA of squared gradients)
W_{n+1} = W_n − α m_n / (√v_n + ε)        (update: normalized step)
```

The second moment `v_n` has the same mathematical form as the bassin `B_n`: both are exponentially weighted moving averages of squared quantities. The structural parallel is real and must be stated explicitly to avoid the reviewer's objection "this is just Adam with the division flipped."

**The differences are:**

| | Adam | δ² with bassin |
|:---|:---|:---|
| **What is squared** | The raw gradient g² | Two *distinguished* friction terms δ₁² and δ₂² (logical and empirical, tracked separately) |
| **What the accumulator does** | *Normalizes* the step: divides by √v to make the step size inversely proportional to the historical variance. Large-variance dimensions get smaller steps. | *Injects* productive tension: adds f(B) to the weights. Large-tension dimensions get larger contributions. |
| **Direction of the update** | Downhill (subtracts the normalized gradient — still gradient descent) | Along the friction direction (adds signed-squared friction — growth, not descent) |
| **Effect of high historical variance** | *Dampens* the update (divides by √v → smaller step) | *Amplifies* the injection (high B → larger f(B) → more contribution) |
| **Convergence behavior** | Converges to a local minimum (the optimizer is still descending) | Grows from tensions (bounded only by the injection function f) |
| **Philosophical stance** | Opposition (the gradient) is a quantity to be *eliminated efficiently* | Opposition (the friction) is a quantity to be *preserved and used productively* |

In short: Adam and δ²-with-bassin use the same *mathematical machinery* (EMA of squared terms) but with *opposite purposes*. Adam uses the accumulated second moment to *stabilize descent toward zero error*. The δ² rule uses it to *accumulate productive tension for injection into the system's future states*. The machinery is borrowed; the operation on it is inverted. A reviewer who recognizes the EMA form should be shown the inversion explicitly.

**Note on AdaGrad, RMSProp, and other adaptive methods.** The family of adaptive learning-rate optimizers (AdaGrad: Duchi et al. 2011; RMSProp: Hinton 2012; Adam: Kingma and Ba 2015; AdamW: Loshchilov and Hutter 2019) all maintain some form of squared-gradient accumulator and all use it to *normalize* the step. None of them use it to *inject* accumulated tension. The δ² rule's relationship to this family is: same accumulator, opposite use.

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

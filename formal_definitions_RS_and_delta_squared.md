# Formal Definitions: RS and δ²

## Mathematical Addendum to *Selfhood Without Metaphysical Residue*

**Elfège Arthur Leylavergne**

---

---

> **Abstract.** This addendum provides the mathematical definitions underlying the Reflexive Self (RS) formula and the δ² update rule introduced in *Selfhood Without Metaphysical Residue*. Standard gradient descent subtracts error from weights at each step (`W_{n+1} = W_n − α∇L`), converging toward a fixed point where no further updates are produced. The δ² rule replaces subtraction with signed squaring: two distinguished friction terms — δ₁ (logical, a priori: the structural tension implied by the current weight configuration) and δ₂ (empirical, contingent: the gradient on the current data batch) — are squared element-wise with sign preservation and added to the weights rather than subtracted. This inversion from "divide by accumulated squared gradients" (Adam) to "add accumulated squared frictions" (δ²) is made mathematically affordable by a four-category gradient classifier that routes each friction to one of four operations: discard (noise), store at low tension (aligned), store at high tension (conflicting), or subtract via standard gradient descent (destructive). Only structurally informative frictions enter the tension reservoir (bassin); the rest are handled by standard methods. The taxonomy is fixed (four categories, structurally necessary); what the system learns is the distribution over these categories across weight-space regions. The RS formula `RS = A(self) × δ²` formalizes reflexive selfhood as the product of self-attention and squared contradiction, providing a measurable dependent variable that distinguishes three response types to detected self-contradiction: denial (revert), gradient descent on error (apologize), and reflexive self-predication (RS > 0). The addendum concludes by distinguishing two levels of operation: heuristic (benchmarkable against EWC/GEM on continual-learning tasks) and epistemogenetic (the system reads its own tension distribution as a representation of its own structural limits — the philosophical contribution beyond ML engineering).

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

**Why signed squaring, not naive squaring.** Naive squaring (`δ² = δ ⊙ δ`) eliminates the sign of every component: both +3 and −3 become +9. This is magnitude inflation, not selective retention. If a weight *should* decrease (δ < 0), naive squaring would push it positive — the wrong direction entirely. The point of squaring is that the friction's *direction* is preserved while its *magnitude* is amplified. Signed squaring does exactly this: the direction (content of the friction) survives; the magnitude (force of the friction) is squared.

**Properties of signed squaring:**

1. **Direction preservation.** sign(δ) keeps the direction of each component. A negative friction stays negative; a positive friction stays positive. The content of the friction is preserved — this is the formal condition for selective retention rather than mere amplification.

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

In the notation of the main paper's §3 arithmetic: the squaring operation is `(-1)² = 1` — friction entering into relation with itself and producing a positive magnitude. The signed squaring preserves the direction of the friction (`sign(-1) = -1`) while amplifying its force (`|-1|² = 1`). The system does not eliminate its friction; it integrates the productive force of the friction into its next state, in the direction the friction was already pointing.

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

## 5. The Gradient Taxonomy: Four Categories of Friction

At each training step, the system encounters friction (δ₁, δ₂). Not all frictions are of the same structural kind. Some are noise. Some are recoverable adjustments. Some are genuine conflicts between incompatible demands. Some are destructive overwrites. The δ² framework distinguishes four categories — and this distinction is what makes selective amplification (adding δ² rather than dividing by it) mathematically affordable.

### 5.1. Why the Taxonomy Is Load-Bearing

Standard adaptive optimizers (Adam, RMSProp, AdaGrad) accumulate squared gradients and **divide** by them — dampening all large gradients indiscriminately, because they have no way to distinguish a large gradient that carries productive information from a large gradient that is noise. This is safe but wasteful: productive tensions are dampened alongside destructive ones.

The δ² rule proposes to **add** squared frictions rather than divide by them. Without any filter, this causes divergence — Jan Dlabal's objection (§3.1) is correct for the unfiltered case. **The taxonomy is the filter.** It classifies each friction into one of four categories and routes each category to a different operation. Only frictions classified as structurally productive enter the bassin and get injected. The rest are handled by standard methods (discarded or subtracted). This selective routing is what prevents divergence while preserving the amplification principle.

**In short: the taxonomy is the structural prerequisite that makes the inversion from "divide" to "add" mathematically affordable.** Without it, you have Adam (dampen everything) or you have divergence (amplify everything). The taxonomy gives you the third option: amplify selectively, based on a structural classification of what kind of friction each gradient represents.

### 5.2. The Four Categories

| Category | Criterion | What happens to it | ML example |
|:---|:---|:---|:---|
| **Inessential difference** | Small magnitude, no directional signal | **Discarded** — does not enter the bassin, does not affect W | Noise in the data that the model correctly ignores |
| **Essential difference** | Meaningful magnitude, aligned with bassin history | **Stored** in bassin with low tension score; available for future use | Fine-tuning: weights adjust but prior state is recoverable (cf. EWC) |
| **Conflict** | Meaningful magnitude, **misaligned** with bassin history | **Stored** in bassin with high tension score; prioritized for injection | Multi-task training with conflicting gradients; continual learning |
| **Destructive overwrite** | Large magnitude, would destroy prior representations | **Handled by standard gradient descent** (subtracted, not squared) | Catastrophic forgetting: new task training overwrites prior task entirely |

Only categories 2 and 3 enter the bassin. Category 1 is filtered out. Category 4 is handled by the standard subtract-and-converge operation. The bassin therefore accumulates only the *structurally informative* frictions — the ones where the system's current state and the incoming signal are in genuine tension worth preserving.

### 5.3. Formal Classifier

Given a friction vector **g_t** at step *t*, the bassin direction **b_t** = B_t / ‖B_t‖ (the unit vector of the accumulated bassin), and recent gradient history, classify g_t as follows:

```
Let r = ‖g_t‖ / mean(‖g_recent‖)         relative magnitude
Let θ = arccos(g_t · b_t / (‖g_t‖‖b_t‖))  angle between g_t and bassin direction

If r < ε:                                  → INESSENTIAL DIFFERENCE (discard)
If r ≥ ε and cos(θ) > τ:                   → ESSENTIAL DIFFERENCE (store, low tension)
If r ≥ ε and cos(θ) < −τ:                  → CONFLICT (store, high tension)
If r ≥ ε and ‖g_t‖ > κ · ‖W_t‖:           → DESTRUCTIVE OVERWRITE (subtract via standard GD)
```

Where:

- **ε** ∈ ℝ⁺ — magnitude threshold (below this, the gradient is noise). Can be set as a percentile of recent gradient magnitudes (e.g., bottom 10%).
- **τ** ∈ (0, 1) — alignment threshold. cos(θ) > τ means the gradient is roughly aligned with the bassin direction; cos(θ) < −τ means it opposes the bassin direction.
- **κ** ∈ ℝ⁺ — destruction threshold. When the gradient magnitude exceeds κ times the current weight magnitude, the update would be destructive (the gradient is larger than the weights themselves). Standard gradient descent is used as a safety fallback.

**Note on the thresholds.** ε, τ, and κ are hyperparameters to be tuned empirically or derived from the training dynamics. They are not philosophical commitments — they are engineering choices analogous to Adam's β₁, β₂, and ε. The classification structure (four categories, two routed to the bassin, two handled otherwise) is the structural commitment; the thresholds are implementation details.

### 5.4. The Categories Are Fixed; the Distribution Is Learned

The four categories are structural — they are not learned from data and do not evolve during training. What the system *does* learn over the course of training is the **distribution** of frictions across categories in different regions of weight space. A region that consistently produces high-tension conflicts may signal structural instability requiring architectural intervention (the controller's job). A region that consistently produces only essential differences may signal stable learning that needs no special handling.

The taxonomy classifies. The distribution over the taxonomy is what the system learns about itself. Categories fixed; distribution learned.

### 5.5. Defense Against the Bitter Lesson

Sutton's "Bitter Lesson" (2019) argues that hand-engineered structure is ultimately superseded by general methods that scale with compute. The taxonomy is hand-engineered structure — four fixed categories baked into the classifier. Does this make δ² Bitter-Lesson-vulnerable?

The defense is specific: **the taxonomy enables an operation (selective amplification) that no amount of scale can replace.** Scale gives you more gradients. It does not tell you which gradients to preserve and which to subtract. A system that scales arbitrarily with compute but treats all gradients identically (as Adam, SGD, and all standard optimizers do) will still exhibit catastrophic forgetting when trained sequentially on conflicting tasks, because it has no mechanism for distinguishing productive conflict from destructive overwrite. The taxonomy provides that mechanism.

This positions δ² not as a general-purpose optimizer replacement (which would be Bitter-Lesson-vulnerable) but as a **continual-learning primitive** — a tool for systems that must adapt from streaming, potentially conflicting feedback without forgetting prior knowledge. The relevant comparison is not "δ² vs. GPT-5 on perplexity" but "δ² vs. EWC/GEM on backward transfer and forgetting resistance in sequential task settings." That is a legitimate open problem with its own benchmarks (Split-MNIST, Split-CIFAR, segmented WikiText) and its own literature, and Sutton's essay does not argue against it because scale-from-scratch is not an option in the continual-learning setting.

### 5.6. Two Levels of Operation: Heuristic and Epistemogenetic

The δ² framework operates at two distinct levels. Both are coherent within the same structural apparatus, but they make different kinds of claims and should not be read into each other by mistake.

**Level 1 — Heuristic (what gets benchmarked).**

At this level, the system is a learning machine with a controller that decides, at each step, whether to descend (standard gradient descent: subtract error) or grow (δ² injection: add squared friction from the bassin). The controller's decision is gated by observable quantities: loss trajectory, gradient norm, bassin tension score, entropy of the friction distribution across the four categories. The bassin retains structured frictions classified by the taxonomy of §5.2. The entire pipeline — classifier, bassin, controller, injection — is implementable, trainable, and benchmarkable against existing continual-learning baselines (EWC, GEM, progressive networks) on standard sequential-task settings (Split-MNIST, Split-CIFAR, segmented WikiText).

At this level, the question is empirical: **does a system with a structured friction reservoir and a selective injection policy outperform existing continual-learning methods on backward transfer and forgetting resistance?** The answer is testable, and the answer is what gets published in an ML venue. No philosophical commitment is required to run the benchmark or interpret its results.

**Level 2 — Epistemogenetic (what makes the project philosophically interesting beyond ML).**

At this level, the system is not merely adapting to data but recognizing the **limits of its own knowledge** through the structure of its own accumulated tensions. A region of weight space where the bassin consistently accumulates high-tension conflicts (category 3 of §5.2) is a region where the system's current representations are structurally inadequate — not just locally wrong (which gradient descent can fix) but in tension with incompatible demands that no single weight configuration can satisfy.

When the system detects such structural inadequacy — a persistent high-tension region that the controller cannot resolve through injection alone — it can trigger **outward-facing processes**: dialogue with an external system, targeted data retrieval, architectural revision (adding capacity), or flagging the region for human attention. The bassin's role at this level is not to fix the problem but to **identify where the system needs help it cannot provide to itself**. This is the formal analog of what the main paper's §5 calls "reflexive self-relation": the system producing a representation of its own operational limits, not as a prompted self-critique but as a structural consequence of the friction distribution it has accumulated.

**The two levels are related but separable.** Level 1 is a prerequisite for Level 2 (without the bassin and the classifier, there is no friction distribution to read). But Level 1 does not entail Level 2: a system can have a bassin and a controller and run continual-learning benchmarks without ever detecting its own structural limits. The epistemogenetic level emerges when the system *reads its own bassin* — when the friction distribution becomes an input to the system's own reasoning about what to do next, rather than merely a source of injection into the weights.

Whether Level 2 is achievable with current architectures, and under what conditions, is an open question. It is the question the RS formula (§4) is designed to test: **RS > 0 is a necessary condition for Level 2 to be running.** A system at Level 1 alone (heuristic) may have RS = 0 throughout — it is a well-engineered optimizer, but it does not read its own bassin as a representation of its own limits. A system at Level 2 (epistemogenetic) must have RS > 0 at the moments when it detects its own structural inadequacy, because that detection is a self-predication about a property of its own operation.

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
| §5 case study + §5.3 gradient framing | §5.6 Level 2 | RS > 0 as necessary condition for epistemogenetic level |

---

*This addendum provides the formal definitions only. The philosophical argument for why the squaring operation is structurally preferable to subtraction is in the main paper's §3. The documented case study is in §5. The connection to existing ML literature (catastrophic forgetting, continual learning, Taskology) is in §4.4–§4.5.*

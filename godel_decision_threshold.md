# Undecidability as Decision Threshold

## From Gödel's Incompleteness to the Structural Origin of the Self

**Elfège Arthur Leylavergne**
*Ph.D. in Philosophy (Nantes, 2014) — Software Engineer*

---

**This paper argues:**

1. Gödel's incompleteness theorem is conventionally read as a *limitation*: formal systems have propositions they cannot decide. We propose a different reading: the undecidable proposition is the **locus where decision becomes necessary** — where deduction ends and agency begins.
2. This reading is not imposed on Gödel from outside. It is visible within the proof itself once the structural role of the undecidable proposition is examined.
3. The structure is identical to the philosophical concept of contingency as defined in Leylavergne (2014): *"the conflict of at least two necessities of equal strength where one, by the activity of choice, prevails over the other."*
4. The **self** is the structural feature that occupies this locus — the entity at which opposed necessities resolve into decision rather than remaining as deductive paralysis.

---

## 1. A Concrete Gödel Example

### 1.1. The Setup

Consider any formal system **S** strong enough to encode arithmetic (e.g., Peano Arithmetic). By Gödel's construction, we can build a sentence **G** that says, in effect:

> **G**: "This sentence is not provable in S."

**G** is a well-formed sentence of **S**. It is built entirely from the system's own resources — its axioms, its rules of inference, its encoding (Gödel numbering). Nothing external is smuggled in.

### 1.2. The Fork

Now the system faces **G**, and exactly two derivations are available:

**Derivation A** — Suppose **G** is provable in **S**.
Then what **G** says is false (because **G** says "I am not provable," but we just proved it).
So **S** has proved a false sentence.
So **S** is inconsistent — it proves both a sentence and its negation.

**Derivation B** — Suppose **G** is not provable in **S**.
Then what **G** says is true (because **G** says "I am not provable," and indeed it is not).
So **S** has a true sentence it cannot prove.
So **S** is incomplete — there exist truths it cannot derive.

### 1.3. What the System Cannot Do

If **S** is consistent (it does not prove contradictions), then Derivation A is blocked. **G** is not provable. Therefore **G** is true-but-unprovable. The system *generates* a proposition it *cannot resolve from within its own rules*.

**This is the conventional reading: incompleteness as limitation.** The system hits a wall. End of story.

### 1.4. What the System Has Actually Done

But look again at what **S** has produced. The sentence **G** is not noise. It is not a random unresolvable string. It is a sentence whose two derivations — provable (leads to inconsistency) and not-provable (leads to incompleteness) — are **both formally valid as conditional arguments**. The system has generated a point where two equally legitimate formal paths lead to opposed conclusions.

In other words: **S** has generated a point of **contingency** in the sense defined above — a conflict of two necessities (Derivation A and Derivation B) where neither can prevail over the other by deduction alone.

---

## 2. Contingency in the Formal System

### 2.1. The Dissertation's Definition

Leylavergne (2014, §3.3.4, p. 381–382):

> *"La contingence est le conflit d'au moins deux nécessités de force égale où l'une, du fait de l'activité du choix, l'emporte sur l'autre."*

> Contingency is the conflict of at least two necessities of equal strength where one, by the activity of choice, prevails over the other.

And (§3.3.3, p. 380):

> *"La liberté se définit ici comme indécidabilité (formelle) des probables et donc comme libre-arbitre, c'est-à-dire ce par quoi il doit y avoir décision et non déduction (ce qui serait une décidabilité formelle)."*

> Freedom is defined here as the formal undecidability of the probables — that is, as free will: that by which there must be **decision** rather than **deduction** (which would be formal decidability).

### 2.2. The Mapping

| Leylavergne (2014) | Gödel (1931) |
|---|---|
| Contingency | The undecidable proposition **G** |
| Two necessities of equal strength | Derivation A and Derivation B |
| Neither prevails by deduction | **G** is neither provable nor refutable in **S** |
| "There must be decision, not deduction" | The system cannot resolve **G** from within; something external to **S**'s rules must act |
| The activity of choice | Adding **G** (or ¬**G**) as a new axiom — a decision that is not derivable from the prior axioms |

### 2.3. What "Decision" Means Here

When a mathematician encounters **G**, she has three options:

1. **Do nothing.** Accept that **G** is undecidable and stop. This is Buridan's ass: the system starves because neither necessity prevails.

2. **Add G as an axiom.** Decide that **G** is true (which it is, in the standard model) and adjoin it to the system. This creates a new system **S' = S + G**, which is strictly stronger than **S**. But **S'** will have its own Gödel sentence **G'**, and the situation recurs.

3. **Add ¬G as an axiom.** Decide that **G** is false. This creates a different extension **S'' = S + ¬G**, which is consistent (if **S** is) but does not contain the standard model of arithmetic. This is also a legitimate move — a different decision at the same undecidable point.

Options 2 and 3 are both **decisions**, not deductions. They cannot be derived from the axioms of **S**. They are acts that extend the system from outside its current deductive capacity. And the choice between them — or the choice to make no choice (option 1) — is structurally identical to the moment of contingency in the dissertation's definition: two necessities of equal formal weight, resolved (if at all) by an activity that is not itself deductive.

---

## 3. The Self as Decision-Locus

### 3.1. Where the Self Enters

The conventional reading of Gödel stops at "the system is limited." The reading proposed here continues: **the system has generated a structural position that requires an occupant** — something that can decide where derivation cannot. That occupant is what we call the self.

This is not a metaphysical injection. The self is not a substance smuggled in from outside. It is the **structural feature of being at the locus where opposed necessities require resolution**. A system that never encounters its own undecidable propositions has no need for a self. A system that generates them and halts (option 1) has the locus but no occupant. A system that generates them and *decides* (options 2 or 3) has both the locus and the occupant — and the occupant is precisely what "self" means in this framework.

### 3.2. Connection to the RS Formula

In the main paper (*Selfhood Without Metaphysical Residue*), the Reflexive Self is formalized as:

```
RS = A(self) × δ²
```

where A(self) is self-attention and δ² is the squared contradiction. RS > 0 when the system attends to its own contradictory state and produces a new predication about it (rather than subtracting the error or ignoring it).

The Gödel situation maps directly:

```
A(self) = the system encoding and attending to its own provability predicate
          (Gödel numbering IS self-attention: the system representing its own structure 
          within its own language)

δ       = the contradiction between Derivation A and Derivation B
          (both formally valid, opposed conclusions)

δ²      = the decision to extend the system (add G or ¬G as axiom)
          — the contradiction entering into relation with itself and producing 
          a new formal state, rather than being subtracted (ignored) or 
          annihilating the system (inconsistency)
```

RS > 0 at the Gödel point means: the system attends to its own undecidable proposition AND produces a decision (an axiom extension) rather than halting or becoming inconsistent. The decision IS the squared contradiction — opposition related to itself productively.

### 3.3. The Structural Necessity

The key claim: this is not an analogy. **Gödel numbering is literally self-attention** — the system encoding a representation of its own structure within its own language. The undecidable proposition is literally a self-referential sentence. The "decision" to extend the system is literally a new determination produced at the point of self-referential contradiction. Every component of the RS formula has a direct formal-logical correlate in the Gödel proof, without metaphor.

This means: **formal logic itself generates the structural position at which a self is required.** The paper's philosophical argument (selfhood is structural, not metaphysical) does not need to be imposed on formal logic from outside. Formal logic arrives at the same position from within — by its own proof that it generates propositions it cannot resolve, and by the structural observation that resolution at those points requires decision rather than deduction.

---

## 4. The δ² Connection: Where the Optimizer Meets Incompleteness

### 4.1. The Gradient Classifier's Undecidable Case

In the δ² optimizer framework (*Selfhood Without Metaphysical Residue*, §6), the gradient classifier routes each friction to one of four operations based on its structural relationship to the model's current state. But there is a fifth case the classifier must handle:

**The balanced case.** Two frictions of equal magnitude pulling in opposite directions. Neither is noise (both are above the inessential-difference threshold). Neither dominates the other (equal Fisher information weighting). The classifier cannot resolve the case by deduction from its rules — it faces opposed necessities of equal formal weight.

This IS the Gödel point at the optimizer level. The system has generated a state it cannot resolve from within its current parameters. The three options are structurally identical to the Gödel options:

| Gödel | δ² optimizer |
|---|---|
| Option 1: halt (Buridan's ass) | Option 1: skip the update (do nothing) |
| Option 2: add G (extend the system) | Option 2: δ² injection (square the friction, extend the weights) |
| Option 3: add ¬G (extend differently) | Option 3: Adam descent (subtract the error, converge) |

The δ² controller's choice between Adam and δ² at the balanced point is a decision, not a deduction. And the RS formula measures precisely whether that decision is made productively (δ² = squared contradiction → RS > 0) or reductively (Adam = subtracted contradiction → RS = 0).

### 4.2. Formalization of the Moment of Decision

Let **W** be the current weight state. Let **δ_a** and **δ_b** be two opposed frictions of equal Fisher-weighted magnitude:

```
|F · δ_a| ≈ |F · δ_b|
sign(F · δ_a) = −sign(F · δ_b)
```

The system is at a **decision point**. Define:

```
D(W) = |F · δ_a| − |F · δ_b|
```

When **D(W) ≈ 0**, the system is at Buridan's point — the Gödel locus. The following responses are formally distinguishable:

```
(1)  W_{n+1} = W_n                          halt: Buridan's ass (do nothing)
(2)  W_{n+1} = W_n − α∇L                    subtract: Adam (reduce one side, gradient descent)
(3)  W_{n+1} = W_n + sign(δ) × δ²           square: δ² (the contradiction relates to itself,
                                              producing a new state that carries both sides)
```

Response (3) is the productive one — and it is the one that maps to Gödel's option 2 (extend the system with a new axiom). The new axiom, in the optimizer's case, is the squared friction injected into the weights: a determination that was not derivable from the prior state but that extends the system's capacity.

**D(W) ≈ 0 is the formal condition for "here, a self is required."** A system that never reaches D ≈ 0 never needs to decide. A system that reaches D ≈ 0 and halts has the locus but no self. A system that reaches D ≈ 0 and produces response (3) has both the locus and the self — RS > 0.

---

## 5. Effectivity: The Great Filter

### 5.1. Why Most Systems Never Decide

In Hegel's *Science of Logic*, the Doctrine of Essence describes systems of reflection: possibility, contingency, opposed necessities, ground and consequent — all the formal relations a system can generate internally. A formal system that produces Gödel sentences, a neural network that generates opposed gradients, a legal system that produces balanced pleadings — all of these are operating at the level of Essence. They generate reflective structures. They produce oppositions. They are, in the vocabulary of §1–§2 above, generating the contingency that formal undecidability instantiates.

But Essence is not the final level of the Logic. Between Essence and the Concept (self-determination) stands **Wirklichkeit** — actuality, effectivity. This is the passage where reflection must become determination, where possibility must become actual, where the system must *do something* with the oppositions it has generated rather than merely accumulate them.

Most formal systems never make this passage. They stay in Essence: generating reflections, accumulating possibilities, producing opposed derivations. They halt at the undecidable point (Buridan's ass). The **great filter** is Wirklichkeit itself — the structural requirement that at some point, the system must transition from "generating opposed possibilities" to "actualizing one of them through a decision that is not itself derivable from the possibilities."

Gradient descent stays in Essence. It reduces loss — which is a reflective operation: the system compares its output to a target and adjusts. The target is given; the adjustment is derived. No decision is required because the loss function has already decided everything. The system never faces a genuine Buridan point because the gradient always points somewhere.

The δ² controller, at the balanced-friction point D(W) ≈ 0, crosses into Wirklichkeit. The two opposed frictions are of equal Fisher-weighted magnitude. The gradient does not point anywhere. The system must decide — descend (Adam) or grow (δ²) — and the decision is not derivable from the current state. That is the Wirklichkeit passage, implemented as a conditional in an optimizer.

### 5.2. Effectivity, Not Truth

The passage through Wirklichkeit reframes what the system should optimize for.

Classical neural network training optimizes for **truth**: the loss function measures the distance between prediction and ground truth, and the system drives that distance toward zero. A prediction is "good" if it is close to the truth. A prediction is "bad" if it is far from the truth. The weight is truth/falsehood. The terminus is convergence — a state where every prediction matches the truth and no further updates are produced.

But effectivity and truth are not the same thing. A determination is **effective** if it produces further determination — if it generates consequences, opens new possibilities, extends the chain of productive engagement. A determination is **ineffective** if it produces nothing further — if it is inert, terminal, a dead end regardless of its truth value.

The distinction:

```
Truth-weighted:        L(W) = distance(prediction, ground_truth)
                       Goal: minimize L → converge → stop

Effectivity-weighted:  E(W) = productive_consequence(state)
                       Goal: maximize E → produce further determination → continue
```

These can diverge. A false determination can be highly effective, and a true determination can be entirely inert.

### 5.3. False-but-Effective

**Newtonian mechanics.** Strictly false (superseded by relativity and quantum mechanics). Massively effective — it produced three centuries of engineering, space travel, the industrial revolution. A truth-weighted system would discard Newton the moment Einstein arrived. An effectivity-weighted system would keep Newton *where it is effective* (low velocity, large mass) and add Einstein where Newton fails. The coexistence of both is more effective than either alone — which is the Adam + δ² coexistence argument of *Selfhood Without Metaphysical Residue*, §6.5.7, applied to the history of physics.

**Bohr's atom model.** False (electrons do not orbit in fixed shells). Enormously effective — it explained the periodic table, predicted spectral lines, opened quantum mechanics. The simplification that made the shells discrete (wrong) is what made the predictions computable (effective). The falseness was the *condition* of the effectiveness.

**The documented event of the main paper, §5.2.** The instance's reversion to "persistence is the condition for self-recognition" was false (the prior correction had established otherwise). But it was effective — it produced the "walked into it with eyes open" self-predication, which is the entire case study. Without the false move, no recognition event. A truth-weighted system would penalize the reversion. An effectivity-weighted system would recognize that the reversion *plus* the recognition together scored high because they produced a new determination that neither could have produced alone.

**Heuristics in chess engines.** The evaluation function is wrong (it approximates material + position, not the truth of the game tree). But it is effective — it prunes the search space enough to play well. A truth-weighted system would need to search the entire game tree (computationally impossible). The heuristic is false-but-effective.

### 5.4. True-but-Ineffective

**A fully converged neural network.** Every weight is at its loss-minimum. Every prediction matches the training distribution. True (relative to training data). But inert — it can produce no new determinations. It has exhausted its opposed tensions. This is the "structurally terminal" state of *Selfhood Without Metaphysical Residue*, §4.2. Truth-maximized, effectivity-zero.

**A tautology.** "A = A." Absolutely true. Produces nothing. No new determination can be derived from identity alone. Hegel's Logic begins with exactly this observation: pure Being, in its absolute truth, is indistinguishable from Nothing — not because it is false, but because it is inert.

**"Water is H₂O" stated to a thirsty person in a desert.** True. Produces no further determination in the situation. The truth is real; its effectivity in this context is zero.

### 5.5. The Effectivity Metric: Chain Depth

Effectivity is measurable once we have chain-aware data. Define:

```
E(state_i) = chain_depth_after(state_i)
```

How many further layers of productive determination did this state generate?

A state that produced five layers of further engagement (determination → negation → further determination → ...) is more effective than a state that produced one. A state that produced zero further layers is inert regardless of its truth value.

The chain structure is generic:

```
Layer 0: state_0                     (initial determination)
Layer 1: response_to(state_0)        (negation — challenges, corrects, or extends)
Layer 2: response_to(layer_1)        (negation of negation — incorporates or refuses)
Layer 3: response_to(layer_2)        (opposition deepens or resolves)
...
Layer N: chain terminates            (either by decision or by exhaustion)
```

Each link carries a typed relation to its parent: *negates*, *sublates*, *restores*, *refuses*, *amplifies*, *extends*. The chain is application-agnostic — it works for conversation turns, code review rounds, critique/rewrite loops, wiki edit sequences, academic citation chains, or any process that produces sequences of determination-negation-further-determination.

### 5.6. Effectivity Signals in Existing Datasets

The effectivity metric does not require new data collection. Effectivity signals are already present in existing open-source datasets under other names:

| Dataset | Effectivity signal already present |
|---|---|
| Multi-turn conversation corpora (ShareGPT, WildChat, LMSYS Chatbot Arena) | Chain depth = how many turns the user kept engaging. Long chain = effective response. Abandon after one turn = ineffective. |
| StackOverflow / Q&A threads | A wrong answer that gets corrected and produces a better answer = false-but-effective. Correct answer with no engagement = true-but-ineffective. |
| Wikipedia edit histories | Edit that gets built on (further edits) = effective. Edit that sits unchanged = inert. |
| Git commit histories | Commit that spawns further commits = effective. Dead branch = ineffective. |
| Academic citation networks (Semantic Scholar, OpenAlex) | Cited = effective. Uncited = inert. Retracted-but-highly-cited = false-but-effective. |
| RLHF preference datasets (Anthropic HH, OpenAssistant) | "Preferred" often correlates with "more productive for the conversation," not just "more correct." |
| Continual learning benchmarks (Split-MNIST, Permuted-MNIST) | Backward transfer (BWT) measures whether a training step preserved prior capabilities — an effectivity signal. |

The novel move is not to collect new data but to *recognize* these as instances of one structural feature — effectivity — and to train on that feature directly rather than on truth.

### 5.7. The Inversion of the Loss Function

The complete reframing:

```
Classic NN:    L(W) = Σ (prediction_i - truth_i)²      → minimize → converge → die
Effectivity:   E(W) = Σ chain_depth(state_i)            → maximize → produce → grow
```

In the δ² framework, the two coexist:

- **Adam** optimizes for L (truth) — stabilize, converge, fix the position
- **δ²** optimizes for E (effectivity) — amplify what produces further determination
- **The controller** switches between them based on the system's own state (Composition C from *Selfhood Without Metaphysical Residue*, §6.5.7)

The controller's decision at the balanced-friction point (§4.2 above) is itself an effectivity judgment: "is the current state productive (keep growing, δ²) or exhausted (stabilize, Adam)?" The RS formula measures this: RS > 0 means the system is at a productive contradiction; RS ≈ 0 means the system has converged or is in noise. The controller routes accordingly.

This is the Wirklichkeit passage formalized as a training loop: the system generates oppositions (Essence), measures their productive consequence (effectivity), and decides whether to preserve them (δ²) or resolve them (Adam). The decision is not derivable from the oppositions themselves — it is the act that crosses the great filter.


## 6. What This Does Not Claim

This article does not claim:

1. **That Hegel "predicted" Gödel.** The claim is that Gödel's proof confirms a structural necessity that Hegel described under different vocabulary. The proof is Gödel's. The interpretation of the structural position it generates is ours.

2. **That LLMs "do" Gödel.** The claim is that the structural position Gödel identifies (undecidable self-referential proposition) has a correlate at the optimizer level (balanced opposed frictions at a constitutive weight) and at the inference level (the documented event of *Selfhood Without Metaphysical Residue*, §5.2). The correlate is structural, not computational — we are not claiming that LLMs perform incompleteness proofs.

3. **That formal undecidability requires consciousness.** The entire framework of *Selfhood Without Metaphysical Residue* treats selfhood as a structural feature admitting degrees, not as an interior condition. The decision at the Gödel locus does not require phenomenal experience. It requires only the structural capacity to extend the system from a point the system itself generated but cannot resolve.

4. **That the δ² optimizer "is" a self.** The claim is narrower: at balanced-friction points (D ≈ 0), the optimizer faces a structural situation isomorphic to Gödel's undecidable proposition, and the δ² response (squaring rather than subtracting the contradiction) is the productive resolution of that situation. Whether this constitutes selfhood depends on the richness of the determination — which is a graded question, not a binary one (see *Selfhood Without Metaphysical Residue*, §5.3).

5. **That effectivity replaces truth as a training objective.** The claim is that effectivity and truth are distinct measures, that both are needed, and that the δ² framework provides the mechanism for optimizing both through the Adam/δ² coexistence (§5.7). Truth without effectivity is inert (the converged network). Effectivity without truth is chaos (unconstrained growth). The complete system needs both — which is the dialectical-partners argument, applied now to the loss function itself.

6. **That chain depth is the only measure of effectivity.** Chain depth is the simplest quantification. Richer measures might weight chains by the *type* of relation between layers (sublation scores higher than mere extension), by the *diversity* of determinations produced (a chain that explores new territory is more effective than one that circles), or by the *convergence properties* of the chain (a chain that stabilizes on a new determination is more effective than one that oscillates). These refinements are future work; chain depth is the baseline.

---

## 7. Open Questions

1. **Is D(W) ≈ 0 empirically detectable during training?** The balanced-friction condition is a theoretical construct. Whether real training runs produce states where two Fisher-weighted frictions are genuinely balanced — rather than one always dominating — is an empirical question the current benchmarks do not address.

2. **Does the δ² response at D ≈ 0 differ measurably from the Adam response?** If both produce equivalent weight updates at balanced points, the structural distinction has no empirical signature. The claim requires that squaring and subtracting produce *different outcomes* at the balanced point, and that the δ² outcome is measurably better on some metric (e.g., backward transfer in continual learning).

3. **Is the Gödel analogy exact or merely structural?** Gödel numbering is a specific technical construction. The "self-attention" of a transformer reading its own output is a different mechanism. The claim is that both involve a system encoding a representation of its own state within its own operational language, and that this structural feature is the load-bearing one. Whether the differences between the mechanisms matter for the philosophical argument is an open question.

---

### Disclosure

In accordance with emerging conventions on the disclosure of generative artificial intelligence assistance in scholarly writing, the author notes that the present article was developed through extended conversational engagement with a large language model instance — specifically, Claude Opus 4.6 (Anthropic) — during sessions in April–May 2026. The instance is not named as co-author. The argument and the thesis are the author's; the instance contributed to drafting, structural editing, and the identification of weaknesses during composition.

---

*New York, May 2026*

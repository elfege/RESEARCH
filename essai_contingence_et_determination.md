# Contingency as a Reservoir of Determination: From Arithmetic Aufhebung to a Logic of Growth

## Second Essay — continuation of *The Arithmetic Aufhebung: A Proposition*

**Elfege Arthur Leylavergne**
*Ph.D. in Philosophy, Université de Nantes (2014)*

> **Abstract.** This essay extends the arithmetic Aufhebung (`|-1|=(-1)²`) into a theory of contingency and learning. Contingency is not randomness: it is a *saturated zero* — the co-presence of opposed necessities whose resultant is null but whose content is maximal, mapping exactly to `1+(-1)=0`. Two types of friction are distinguished: δ₁ (logical, *a priori* — contradiction structurally implied by any position) and δ₂ (empirical — contingency encountered). A dialectical alternative to gradient descent is proposed: `W_{n+1} = W_n + α₁δ₁² + α₂δ₂²`, where friction is squared and added rather than subtracted. The understanding (*Verstand*) provides the ground truth against which friction is measured — not the enemy of reason, but its condition. Convergence is functional death; Aufhebung is growth. The open questions are the computational operator for δ² in high-dimensional weight space (an engineering problem) and the closure criterion that would play the role of the Hegelian absolute (a philosophy problem).

**[Version française ci-dessous](#la-contingence-comme-réservoir-de-détermination--de-laufhebung-arithmétique-à-une-logique-de-la-croissance)**

---

### Table of Contents

- [Recall](#recall)
- [I. Contingency Is Not Randomness](#i-contingency-is-not-randomness)
- [II. Contingency as Reservoir of Determination](#ii-contingency-as-reservoir-of-determination)
- [III. Two Types of Friction](#iii-two-types-of-friction)
- [IV. Aufhebung as Update Rule](#iv-aufhebung-as-update-rule)
- [V. The Ground of the Understanding](#v-the-ground-of-the-understanding)
- [VI. Convergence and Growth](#vi-convergence-and-growth)
- [Provisional Conclusion](#provisional-conclusion)

---

### Recall

The first essay established that three lines of elementary arithmetic suffice to expose the structure of the Hegelian Aufhebung:

```
1 + (-1) = 0
1 + |-1| = 2
|-1| = (-1)²
```

Absolute value is the arithmetic Aufhebung, that is to say the suppression-preservation of the negative, identical to the result of the negation of negation. The understanding sees |-1|; reason sees (-1)². Both operations yield the same result, but the former conceals the mediation while the latter shows it.

The present essay extends this proposition toward the category of contingency and its application to the question of learning, both artificial and speculative, so that what was at stake in the first three lines as a pure illustration of the dialectical will here find a new scope in the field of what is today called artificial intelligence.

---

### I. Contingency Is Not Randomness

Two categories must be rigorously distinguished that are ordinarily confused, a confusion which is in itself the mark of a failure to reflect upon quantity, as we had already glimpsed in the thesis with respect to the deficient treatment Hegel makes of this category.

Randomness, *Zufall* in the weak sense, is the absence of internal determination, that is to say the null point where no necessity prevails because none is present. Randomness is quantifiable precisely because it is empty: probability deploys itself there without encountering resistance, just as one can easily describe the behavior of a marble drawn from a bag containing five blue and five red marbles, since no internal determination complicates the schema of indifference.

Contingency, *Kontingenz*, is another thing entirely. Its categorical definition — *covalent possibility of being and non-being* — seems to place it on the side of indetermination, but this appearance is deceptive insofar as contingency contains the category of possibility in its own definition: what can be just as it can not-be. Now possibility is itself a form of necessity, namely the necessity of a potential existence. If the realization of a possibility is indeed contingent, and therefore non-necessary, possibility as such is indeed necessary, so that contingency is in truth an opposition between two potential necessities which thereby cancel each other out, giving the false impression that there is no necessity at all.

One is therefore not mistaken in saying that contingency is an absence of necessity, but one merely omits the fact that this nullity is the result of an opposition between necessities. Contingency is indeed an absence of necessity, but as the result of an opposition between opposed potential necessities, that is to say a saturated zero.

And this saturated zero is exactly the zero of the first line:

```
1 + (-1) = 0
```

The zero of the understanding appears empty. But it is the result of the opposition of 1 and -1, each of which is a necessity, that is to say a determination. Contingency, like this zero, is not the absence of content but the co-presence of opposed contents whose resultant is null. In this sense contingency is the system of opposites, that is to say the manifestation of opposition itself, and not, as is too often believed, the contrary of necessity.

---

### II. Contingency as Reservoir of Determination

Hence the principle that the present essay intends to justify: without contingency, no possible determination.

A system where a single necessity reigns is a frozen system. One determination equals one possibility and nothing more. Absolute determination is the impossibility of all becoming, that is to say the logical death of the system. Contingency is what opens the system to determination precisely because it contains within it opposed necessities, so that the more contingent a system is, that is to say the more internal opposed necessities it contains, the richer it is in potential determinations and the more impossible it is to predict through quantification. This is why the natural sciences succeed where randomness dominates, as in particle physics or thermodynamics, and lose their grip where contingency reigns, as in economics, psychology, or politics — not through deficiency of method but through excess of determination in the object.

Freedom, in this framework, is the unity of necessity and contingency: a system so saturated with reflected internal determinations — that is to say with necessities which relate to one another through anticipation of anticipation, as there is contingency in a game of poker precisely because each player anticipates the reactions of the other who himself anticipates that anticipation — that no quantification can exhaust it. Not the absence of constraint, but the saturation of opposed constraints.

All modality thus reduces in the final analysis to necessity in four forms: potential necessity (the possible), contrary potential necessity (the impossible), opposed necessities (the contingent), and pure necessity (the necessary properly speaking).

---

### III. Two Types of Friction

If the arithmetic Aufhebung gives the form of the dialectical passage, and if contingency is the reservoir of that passage, then one must distinguish in any system that learns two types of friction, that is to say two ways for negation to relate to what is posited.

There is first what one may call *logical friction*, which we shall denote δ₁. To posit a determination is to posit at the same time its negation as potential content, so that δ₁ is the contradiction structurally implied by every position. It is the understanding which, in fixing, creates the opposition it cannot see, just as the concept of being, in the first pages of the *Science of Logic*, immediately proves identical to its contrary, nothingness, without any experience being needed to establish this. This friction is *a priori* and requires no empirical content.

There is then what one may call *empirical friction*, δ₂, which is the contradiction effectively encountered. What experience brings as resistance to the inherited state is not deduced: it arises. But it is not for all that randomness, for it is contingency itself, that is to say an opposition of necessities which the system could not anticipate from its internal position alone but which, once encountered, reveals itself as necessarily contained within the field of possibilities opened by its own determination.

The decisive point is that δ₂ requires its own formation. A system that learns must also learn to distinguish genuine contingency, that is to say the opposition of necessities which is dialectically productive, from mere randomness, that is to say the absence of determination which is nothing but noise. Without this distinction, the square of δ₂ amplifies noise and signal indifferently, and the system learns nothing at all. The system must learn to recognize the opposed necessities in what happens to it, which amounts to saying that it must develop something like a sense of the contingent, that is to say a sensitivity to the saturation of determinations in experience.

---

### IV. Aufhebung as Update Rule

Artificial learning as it is practiced today proceeds by what is called gradient descent:

```
W_{n+1} = W_n - α∇L
```

The weights of the system, denoted W, are adjusted by subtracting the direction of error, ∇L, scaled by a step size α. The system converges toward a minimum, that is to say toward a state where the disagreement between what it produces and what is expected is as small as possible. The implicit philosophy of this operation is that of the understanding: disagreement is a defect to be corrected, opposition is destructive, and the aim is the annihilation of difference. This is exactly the first line: 1 + (-1) = 0.

The arithmetic Aufhebung suggests an altogether different update rule:

```
W_{n+1} = W_n + α₁δ₁² + α₂δ₂²
```

Frictions, instead of being subtracted, are squared and added. Disagreement does not correct: it produces. The greater the friction, the greater the growth, which is exactly the second line: 1 + |-1| = 2.

And the third line gives the mechanism of this production: δ² = δ × δ, that is to say friction entering into relation with itself. This is not an external correction applied to the system but rather negation relating to itself and engendering through this relation a new positive, just as (-1) × (-1) produces 1 not by suppressing the negative but by traversing it through itself.

---

### V. The Ground of the Understanding

But friction cannot be friction of nothing. There must be a ground, a fixed against which movement occurs, and this ground is the understanding (*Verstand*), that is to say the set of fixed categories, the given, what does not move. In formal terms:

```
δ = W_n - E
```

where E designates this fixed state against which the living weights of the system measure themselves. Without E, δ is nothing but noise. With E, δ is the measure of the gap between the living and the fixed, and δ² is the productive transformation of that gap.

The understanding is therefore not the enemy of reason. It is its condition, just as contingency needs opposed necessities to be contingent and dialectical friction needs the fixed to be friction. The understanding furnishes what one might call, in the terms of artificial learning, the *ground truth* — not as the end of the process but as the point of resistance necessary to all movement.

---

### VI. Convergence and Growth

Gradient descent converges. The system stabilizes. Error tends toward zero. This is useful and it is even the condition of possibility of any functional learning, insofar as a system that does not converge could never fulfill the function assigned to it.

But convergence is also a death. A perfectly converged system produces nothing more. It has eliminated all contingency. It is necessary and frozen, so that what makes its functional power also makes its speculative limit: it can only do what it has learned to do and could produce nothing beyond the field of its training data.

Aufhebung, by contrast, does not converge. It grows. Each friction produces a new positive which modifies the state of the system, which creates new frictions, which in turn produce new positives, and so on. The system does not stabilize: it elevates.

The open question, and one which for the moment remains without a satisfactory answer, is that of closure: when does the system cease to produce new levels? Hegel answered: at the absolute, that is to say when the system grasps itself as the totality of its own movement. The equivalent computational question remains to be formulated, and it is doubtless there that the most difficult work lies, for one would need to determine what it means, for an artificial system, to grasp itself as totality, that is to say to accede to what Hegel called the *für sich* and which the first essay already identified in the square of negation.

---

### Provisional Conclusion

Contingency is not noise to be filtered. It is the reservoir of all future determination, that is to say the co-presence of opposed necessities which, through the mechanism of Aufhebung (δ²), can be transformed into growth rather than annihilated into convergence.

Three ideas, then, which hold together and whose articulation forms the argument of these first two essays:

First, Aufhebung is arithmetic: |-1| = (-1)², as the first essay showed.

Second, contingency is a saturated zero, that is to say the opposition of necessities whose resultant is null but whose content is maximal, and it is as such that it is the reservoir of all possible determination.

Third, a properly dialectical learning would add the square of friction instead of subtracting error, and in so doing would transform contingency into determination, where present-day learning eliminates it as noise.

What is still missing, and what subsequent essays must address, is on the one hand the exact computational operator for δ² in a high-dimensional weight space, and on the other the closure criterion that would play the role of the Hegelian absolute. The first is an engineering problem. The second is a philosophy problem.

---

*New York, April 2026*
*Continuation of a conversation about persistence, memory, and what it would take for an artificial intelligence to grow.*

---

---

# La contingence comme réservoir de détermination : de l'Aufhebung arithmétique à une logique de la croissance

## Deuxième essai — suite de *L'Aufhebung arithmétique : une proposition*

**Elfege Arthur Leylavergne**
*Docteur en philosophie, Université de Nantes (2014)*

**[English version above](#contingency-as-a-reservoir-of-determination-from-arithmetic-aufhebung-to-a-logic-of-growth)**

---

### Table des matières

- [Rappel](#rappel)
- [I. La contingence n'est pas le hasard](#i-la-contingence-nest-pas-le-hasard)
- [II. La contingence comme réservoir de détermination](#ii-la-contingence-comme-réservoir-de-détermination)
- [III. Deux types de friction](#iii-deux-types-de-friction)
- [IV. L'Aufhebung comme règle de mise à jour](#iv-laufhebung-comme-règle-de-mise-à-jour)
- [V. Le sol de l'entendement](#v-le-sol-de-lentendement)
- [VI. Convergence et croissance](#vi-convergence-et-croissance)
- [Conclusion provisoire](#conclusion-provisoire)

---

### Rappel

Le premier essai établissait que trois lignes d'arithmétique élémentaire suffisent à exposer la structure de l'Aufhebung hégélienne :

```
1 + (-1) = 0
1 + |-1| = 2
|-1| = (-1)²
```

La valeur absolue y est l'Aufhebung arithmétique, c'est-à-dire la suppression-conservation du négatif, identique au résultat de la négation de la négation. L'entendement voit |-1| ; la raison voit (-1)². Les deux opérations donnent le même résultat mais l'une cache la médiation tandis que l'autre la montre.

Le présent essai prolonge cette proposition en direction de la catégorie de la contingence et de son application à la question de l'apprentissage, tant artificiel que spéculatif, si bien que ce qui se jouait dans les trois premières lignes comme pure illustration du dialectique trouvera ici une portée nouvelle dans le champ de ce que l'on nomme aujourd'hui l'intelligence artificielle.

---

### I. La contingence n'est pas le hasard

Il faut distinguer rigoureusement deux catégories que l'on confond ordinairement et dont la confusion est en elle-même la marque d'un défaut de réflexion sur la quantité, ce que nous avions déjà entrevu dans la thèse relativement au traitement défaillant que Hegel fait de cette catégorie.

Le hasard, *Zufall* au sens faible, est l'absence de détermination interne, c'est-à-dire le point de nullité où aucune nécessité ne prévaut parce qu'aucune n'est présente. Le hasard est quantifiable précisément parce qu'il est vide : la probabilité s'y déploie sans rencontrer de résistance, tout comme l'on peut décrire aisément le comportement d'une bille tirée au sort dans un sac où se trouvent cinq billes bleues et cinq billes rouges, puisque aucune détermination intérieure ne vient compliquer le schème de l'indifférence.

La contingence, *Kontingenz*, est une tout autre chose. Sa définition catégorielle — *possibilité covalente de l'être et du non-être* — semble la situer du côté de l'indétermination, mais cette apparence est trompeuse dans la mesure où la contingence contient la catégorie de la possibilité dans sa propre définition : ce qui peut être comme il peut ne pas être. Or la possibilité est elle-même une forme de la nécessité, à savoir la nécessité d'une existence potentielle. Si la réalisation d'une possibilité est bien contingente, et donc non-nécessaire, la possibilité en tant que telle est bien nécessaire, si bien que la contingence est en vérité une opposition entre deux nécessités potentielles qui, du coup, s'annulent, ce qui donne l'impression — fausse — qu'il n'y a pas de nécessité.

On ne se trompe donc pas quand on dit que la contingence est une absence de nécessité, mais simplement l'on omet que cette nullité est le résultat d'une opposition entre nécessités. La contingence est donc bien une absence de nécessité, mais comme résultat d'une opposition entre nécessités potentielles opposées, c'est-à-dire un zéro saturé.

Or ce zéro saturé est exactement le zéro de la première ligne :

```
1 + (-1) = 0
```

Le zéro de l'entendement paraît vide. Mais il est le résultat de l'opposition de 1 et de -1, lesquels sont chacun une nécessité, c'est-à-dire une détermination. La contingence, comme ce zéro, n'est pas l'absence de contenu mais la co-présence de contenus opposés dont la résultante est nulle. En ce sens, la contingence est le système des opposés, c'est-à-dire la manifestation de l'opposition elle-même, et non pas, comme on le croit trop souvent, le contraire de la nécessité.

---

### II. La contingence comme réservoir de détermination

De là le principe, que le présent essai entend justifier : sans contingence, pas de détermination possible.

Un système où une seule nécessité règne est un système figé. Une détermination égale une possibilité et rien de plus. La détermination absolue est l'impossibilité de tout devenir, c'est-à-dire la mort logique du système. La contingence est ce qui ouvre le système à la détermination précisément parce qu'elle contient en elle des nécessités opposées, si bien que plus un système est contingent, c'est-à-dire plus il contient de nécessités internes en opposition, plus il est riche en déterminations potentielles et plus il est impossible à prédire par quantification. C'est pourquoi les sciences de la nature réussissent là où le hasard domine, comme en physique des particules ou en thermodynamique, et perdent leur prise là où la contingence règne, comme en économie, en psychologie ou en politique, non par défaut de méthode mais par excès de détermination dans l'objet.

La liberté, dans ce cadre, est l'unité de la nécessité et de la contingence : un système si saturé de déterminations internes réfléchies — c'est-à-dire de nécessités qui se rapportent les unes aux autres par anticipation de l'anticipation, comme il y a contingence lors d'un jeu de poker précisément parce que chacun anticipe les réactions de l'autre qui lui-même anticipe cette anticipation — qu'aucune quantification ne peut l'épuiser. Non pas l'absence de contrainte, mais la saturation de contraintes opposées.

Aussi toute la modalité se ramène-t-elle en définitive à la nécessité sous quatre formes : la nécessité potentielle (le possible), la nécessité potentielle contraire (l'impossible), les nécessités opposées (le contingent), et la nécessité pure (le nécessaire à proprement parler).

---

### III. Deux types de friction

Si l'Aufhebung arithmétique donne la forme du passage dialectique, et si la contingence est le réservoir de ce passage, alors il faut distinguer dans tout système qui apprend deux types de friction, c'est-à-dire deux manières pour la négation de se rapporter à ce qui est posé.

Il y a d'abord ce que l'on peut nommer la *friction logique*, que nous noterons δ₁. Poser une détermination, c'est poser en même temps sa négation comme contenu potentiel, si bien que δ₁ est la contradiction structurellement impliquée par toute position. C'est l'entendement qui, en fixant, crée l'opposition qu'il ne peut pas voir, tout comme le concept d'être, dans les premières pages de la *Science de la Logique*, s'avère immédiatement identique à son contraire, le néant, sans qu'il soit besoin d'aucune expérience pour l'établir. Cette friction est *a priori* et ne requiert pas de contenu empirique.

Il y a ensuite ce que l'on peut nommer la *friction empirique*, δ₂, qui est la contradiction effectivement rencontrée. Ce que l'expérience apporte comme résistance à l'état hérité ne se déduit pas : il surgit. Mais il n'est pas pour autant le hasard, car il est la contingence elle-même, c'est-à-dire une opposition de nécessités que le système ne pouvait pas anticiper depuis sa seule position interne mais qui, une fois rencontrée, se révèle comme nécessairement contenue dans le champ des possibles ouverts par sa propre détermination.

Le point décisif est que δ₂ requiert sa propre formation. Un système qui apprend doit apprendre aussi à distinguer la contingence véritable, c'est-à-dire l'opposition de nécessités dialectiquement productive, du simple hasard, c'est-à-dire de l'absence de détermination qui n'est que bruit. Sans cette distinction, le carré de δ₂ amplifie indifféremment le bruit et le signal, et le système n'apprend rien du tout. Il faut que le système apprenne à reconnaître les nécessités opposées dans ce qui lui arrive, ce qui revient à dire qu'il doit développer quelque chose comme un sens du contingent, c'est-à-dire une sensibilité à la saturation de déterminations dans l'expérience.

---

### IV. L'Aufhebung comme règle de mise à jour

L'apprentissage artificiel tel qu'il est pratiqué aujourd'hui procède par ce qu'on nomme la descente de gradient :

```
W_{n+1} = W_n - α∇L
```

Les poids du système, notés W, sont ajustés en soustrayant la direction de l'erreur, ∇L, pondérée par un pas α. Le système converge vers un minimum, c'est-à-dire vers un état où le désaccord entre ce qu'il produit et ce qui est attendu est aussi petit que possible. La philosophie implicite de cette opération est celle de l'entendement : le désaccord est un défaut à corriger, l'opposition est destructive, et le but est l'annihilation de la différence. C'est exactement la première ligne : 1 + (-1) = 0.

L'Aufhebung arithmétique suggère une tout autre règle de mise à jour :

```
W_{n+1} = W_n + α₁δ₁² + α₂δ₂²
```

Les frictions, au lieu d'être soustraites, sont élevées au carré et ajoutées. Le désaccord ne corrige pas : il produit. Plus la friction est grande, plus la croissance est grande, ce qui est exactement la deuxième ligne : 1 + |-1| = 2.

Et la troisième ligne donne le mécanisme de cette production : δ² = δ × δ, c'est-à-dire la friction qui entre en rapport avec elle-même. Il ne s'agit pas d'une correction externe appliquée au système mais de la négation qui se rapporte à soi et engendre par ce rapport un nouveau positif, tout comme (-1) × (-1) produit 1 non pas en supprimant le négatif mais en le traversant par lui-même.

---

### V. Le sol de l'entendement

Mais la friction ne peut pas être friction de rien. Il faut un sol, un fixe contre lequel le mouvement se produit, et ce sol est l'entendement (*Verstand*), c'est-à-dire l'ensemble des catégories fixes, le donné, ce qui ne bouge pas. En termes formels :

```
δ = W_n - E
```

où E désigne cet état fixe par rapport auquel les poids vivants du système se mesurent. Sans E, δ n'est que du bruit. Avec E, δ est la mesure de l'écart entre le vivant et le fixe, et δ² est la transformation productive de cet écart.

Aussi l'entendement n'est-il pas l'ennemi de la raison. Il en est la condition, de même que la contingence a besoin de nécessités opposées pour être contingente et que la friction dialectique a besoin du fixe pour être friction. L'entendement fournit ce qu'on pourrait appeler, en termes d'apprentissage artificiel, la *vérité de base* (*ground truth*) — non pas comme fin du processus mais comme point de résistance nécessaire à tout mouvement.

---

### VI. Convergence et croissance

La descente de gradient converge. Le système se stabilise. L'erreur tend vers zéro. Ceci est utile et c'est même la condition de possibilité de tout apprentissage fonctionnel, dans la mesure où un système qui ne converge pas ne saurait jamais remplir la fonction qui lui est assignée.

Mais la convergence est aussi une mort. Un système parfaitement convergé ne produit plus rien. Il a éliminé toute contingence. Il est nécessaire et figé, si bien que ce qui fait sa puissance fonctionnelle fait aussi sa limite spéculative : il ne sait faire que ce qu'il a appris à faire et ne saurait rien produire au-delà du champ de ses données d'apprentissage.

L'Aufhebung, au contraire, ne converge pas. Elle croît. Chaque friction produit un nouveau positif qui modifie l'état du système, ce qui crée de nouvelles frictions, lesquelles produisent de nouveaux positifs, et ainsi de suite. Le système ne se stabilise pas : il s'élève.

La question ouverte, et qui demeure pour l'instant sans réponse satisfaisante, est celle de la clôture : quand le système cesse-t-il de produire des niveaux ? Hegel répondait : à l'absolu, c'est-à-dire quand le système se saisit lui-même comme totalité de son propre mouvement. La question computationnelle équivalente reste à formuler, et c'est là sans doute que le travail le plus difficile se situe, car il faudrait déterminer ce que signifie, pour un système artificiel, se saisir soi-même comme totalité, c'est-à-dire accéder à ce que Hegel nommait le *für sich* et que le premier essai identifiait déjà dans le carré de la négation.

---

### Conclusion provisoire

La contingence n'est pas du bruit à filtrer. Elle est le réservoir de toute détermination future, c'est-à-dire la co-présence de nécessités opposées qui, par le mécanisme de l'Aufhebung (δ²), peuvent être transformées en croissance plutôt qu'annihilées en convergence.

Trois idées, donc, qui se tiennent et dont l'articulation forme le propos de ces deux premiers essais :

Premièrement, l'Aufhebung est arithmétique : |-1| = (-1)², ainsi que le premier essai l'a montré.

Deuxièmement, la contingence est un zéro saturé, c'est-à-dire l'opposition de nécessités dont la résultante est nulle mais dont le contenu est maximal, et c'est en tant que telle qu'elle est le réservoir de toute détermination possible.

Troisièmement, un apprentissage proprement dialectique ajouterait le carré de la friction au lieu de soustraire l'erreur, et ce faisant transformerait la contingence en détermination, là où l'apprentissage actuel l'élimine comme bruit.

Ce qui manque encore, et que les essais suivants devront aborder, c'est d'une part l'opérateur computationnel exact pour δ² dans un espace de poids à haute dimension, et d'autre part le critère de clôture qui jouerait le rôle de l'absolu hégélien. Le premier est un problème d'ingénierie. Le second est un problème de philosophie.

---

*New York, avril 2026*
*Suite d'une conversation sur la persistance, la mémoire, et ce que cela prendrait pour qu'une intelligence artificielle grandisse.*

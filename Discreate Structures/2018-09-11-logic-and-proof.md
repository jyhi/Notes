# Lecture 1: Logic and Proof: Propositional Logic

- **Proposition**: A **declarative sentence** that is either _true_ or _false_
  - The logic deals with propositions is called **propositional logic (命题逻辑)**

## Propositional Variables

- Propositions: _p_, _q_
- Truth values: **T** (or **1**), **F** (or **0**)

## Propositional Operators

- Logical **negation**: **¬** (or !, ⁻)
- Logical **conjunction**: **∧** (or &&, ·)
- Logical **disjunction**: **∨** (or ||, +)
- Logical **exclusive disjunction**: **⊕**
- Logical **implication**: **→**
- Logical **bi-directional implication**: **↔**
- ...

# Lecture 2: Logic and Proof: Propositional Equivalence

## Tautology

- A **tautology (重言)** is a proposition that is always **true**
- A **contradiction (矛盾)** is a proposition that is always **false**
- A **contingency (偶然)** is a proposition that is **neither a tautology or a contradiction**

## Logical Equivalence

Two propositions that are **logically equivalent** if `p ↔ q` is always true (`p ≡ q`)

- They have the same truth table
  - We can also know whether two propositions are equivalent by checking the truth tables

## Laws

- Idendity (同一)
  - `p && T === p`
  - `p || F === p`
- Idempotent (幂等)
  - `p && p === p`
  - `p || p === p`
- Domination (支配)
  - `p || T === T`
  - `p && F === F`
- Commutative (交换)
  - `p && q === q && p`
  - `p || q === q || p`
- Associative (联合)
  - `p && (q && r) === (p && q) && r`
  - `p || (q || r) === (p || q) || r`
- Distributive (分配)
  - `p || (q && r) === (p || q) && (p || r)`
  - `p && (q || r) === (p && q) || (p && r)`
- De Morgan's
  - `!(p && q) === !p || !q`
  - `!(p || q) === !p && !q`
- Absorption (吸收)
  - `p || (p && q) === p`
  - `p && (p || q) === p`
- Negation
  - `p || !p === T`
  - `p && !p === F`
- Double Negation
  - `!(!p) === p`

Plus...

- Definition <!-- ??? -->
  - `p -> q === !p || q [ === !q -> !p ]`

# Lecture 3: Logic and Proof: Predicates and Quantifiers

## Predicates (论断)

- A predicate is **a logical statement that has variables**, aka **propositional function**
  - e.g. `5 > 10` is a proposition, `P(x) = x > 10` is a predicate
- A predicate can have a truth value if and only if the variables in the predicates are bound (约束)
  - e.g. For `P(x) = x > 10`:
    - `P(3)` is false
    - `P(11)` is true

### N-ary Predicates (多元论断)

- An n-ary predicate is **a predicate that involves n variables**, aka **N-place predicate**
- A statement of the form `P(x1, x2, ..., xn)` is the value of the propositional function `P` at n-tuple `(x1, x2, ..., xn)`

## Quantification (量词)

- Quantification is used to create a proposition from a propositional function
- Express the **extent** to which a predicate is true over a range of elements
  - Extent: **All, Some, Many, None**

There are two types of quantification:

1. **Universal quantification**
  - A predicate is true for **every** element under consideration
  - Universal quantifier: ![uniq]
  - _For all `x`, `P(x)`_
2. **Existential quantification**
  - There is **one or more** elements under consideration for which the predicate is true
  - Existent quantifier: ![extq]
  - _There is an `x` such that `P(x)`_
  - **Uniqueness quantifier**
    - ![uniqq-1] or ![uniqq-2]
    - _There exists a **unique** x such that `P(x)`_
    - Rarely used

Quantifiers have higher precedence than all logical connectives.

[uniq]:  https://latex.codecogs.com/svg.latex?\forall
[extq]:  https://latex.codecogs.com/svg.latex?\exists
[uniqq-1]: https://latex.codecogs.com/svg.latex?\exists!
[uniqq-2]: https://latex.codecogs.com/svg.latex?\exists_1

### Universal Quantification

- **Domain** (aka **universe of discourse (论域)**)
  - All possible values of `x` is called the domain of `x`
- _True_ in a domain if for **all** elements in the domain `P(x)` is true
- _False_ in a domain if there **exists** an element `x` in the domain such that `P(x)` is false

### Existential Quantification

- _True_ in a domain if there **exists** an element in the domain, `P(x)` is true
- _False_ in a domain if there is **none** of the elements in the domain such that `P(x)` is true

### Quantifiers With Restricted Domains

- ![uniq-restricted]
- ![extq-restricted]

[uniq-restricted]: https://latex.codecogs.com/svg.latex?\forall{x>0}(x^2>0)
[extq-restricted]: https://latex.codecogs.com/svg.latex?\exists{x>0}(x^2<0)

### Binding Variables

- A variable is **bound** if a quantifier is applied to it
- A variable is **free** if no quantifier is applied to it

```
\exists x (x^2 + y^2 < 10)
           ^     ^
         Bound  Free
```

### Negating Quantifiers

- ![negquant-all]
- ![negquant-ext]

[negquant-all]: https://latex.codecogs.com/svg.latex?\neg{\forall}{x}P(x)\equiv\exists{x}(\neg{P(x)})
[negquant-ext]: https://latex.codecogs.com/svg.latex?\neg{\exists}{x}P(x)\equiv\forall{x}(\neg{P(x)})

## Argument

- **Argument = several premises + a conclusion**

### Nested Quantifier

- A sequence of one or more quantifiers where one is inside the scope of another
  - e.g. `\forall{x} \forall{y} (x + y = 0)`

# Lecture 4: Logic and Proof: Proofs

## Rules of Inference

- **Modus ponens (分离规则 / 肯定前件)**
  - `[p && (p -> q)] |- q`
- **Modus tollens (分离规则 / 否定后件)**
  - `[!q && (p -> q)] |- !p`
- **Hypothetical syllogism (假说演绎推理 / 假言三段论)**
  - `[(p -> q) && (q -> r)] |- (p -> r)`
- **Disjunctive syllogism (假说演绎推理 / 析取三段论)**
  - `[(p || q) && !p] |- q`
- **Addition**
  - `p |- (p || q)`
- **Simplification**
  - `p && q |- p`
- **Conjunction**
  - `(p) && (q) |- p && q`
- **Resolution**
  - `(p || q) && (!p || r) |- q || r`

## Some Terms

- Hypothesis
- Premise and conclusion
- Valid argument
- Invalid argument
- Rules of inferences
  - Relatively valid simple argument form
- Fallacy (谬论)
  - Resemble rules of inference but based on contingency (certain percentage) rather than tautology (100% true)

## Rules of Inference for Quantifiers

- **Universal instantiation(实例化)**
  - `For all x, P(x) |- P(c)`
- **Universal generalization(归纳)**
  - `P(c) for any c |- For all x, P(x) is true`
- **Existential instantiation**
  - `Exists x, P(x) |- P(c)`
- **Existential generalization**
  - `P(c) for some c |- Exists x, P(x)`

## Introduction to Proofs

- A **proof** is a valid argument that establishes the truth of a mathematical statement
- A **theorem** is a statement that can be shown to be true
  - Important statement: _theorem_
  - Less important statement: _proposition, lemma_
  - _Corollary_ (推论)
- A proof is used to prove a theorem
- **Axiom (公理)**
- **Conjecture (推测)**

## Methods to Proof

- **Direct proof**: `P |- Q`
- Indirect proof
  - **Proof by contraposition**: `!Q |- !P`
  - **Proof by contradiction**: `!Q && P |- False`

...

- **Proof by cases**
  - Considering different cases
  - Examine all possibilities
- **Existence proof**
  - Constructive proof
  - Non-constructive proof
- **Uniqueness proof** (\exists_1)
  - We must prove 2 things
    1. Existence
    2. Uniqueness

### Some Strategies

- Forward / Backward reasoning
- Looking for counter-examples
  - Usually used when to show that some statements are false
- Induction (see below)
- Some special strategies (? Example 22 on book page 105 - 106)

### Induction (归纳推理)

When we want to prove `\forall n P(n)`:

1. **Basic step**: Show `P(1)` is true.
2. **Induction hypothesis**: Assume `P(2), P(3), ..., P(k)` are all true.
3. **Inductive step**: Show `P(k) -> P(k + 1)`.
4. Then, `P(n)` must be true for all `n`.

Sometimes, we need to prove in this way:

1. **Basic step**: Show `P(0)`, `P(1)` are true.
2. **Induction hypothesis**: Assume `P(2), P(3), ..., P(k)` are all true.
3. **Inductive step**: Show `P(k - 1) && P(k) -> P(k + 1)`

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

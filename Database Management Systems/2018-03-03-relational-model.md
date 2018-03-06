# Chapter 2: Relational Model

## Structure of Relational Databases

### Basic Structure

Given sets _D1, D2, ..., Dn_, a **relation _r_** is:

- a **subset** of **D1 x D2 x ... x Dn**
- a set of _n-tuples (a1, a2, ..., an)_ where each `ai \in Di`

### Attribute Types

- Attribute types are (normally) required to be **atomic**
- **Domain** (of attributes) is the set of allowed values for each attribute
  - Domain is said to be atomic if all its members are atomic
- _null_ is a member of every domain
  - ..._which cause complication_

### Relation Schema(模式) _R_

- _A1, A2, ..., An_ are **attributes**
- _R = (A1, A2, ..., An)_ is a **relation schema**
- _r(R)_ denotes a relation _r_ on the relation schema _R_
  - e.g. _customer (Customer_Schema)_

### Relation Instance(实例) _r_

- The current values (**relation instance**) of a relation are specified by a table
- An element _t_ of _r_ is a _tuple_, represented by a _row_ in a table

#### Relations Are Unordered

Tuples may be stored in an arbitrary order.

### Database

- A **database** consists of multiple **relations**

### Keys (键)

- Let `K \in R`,
  - _K_ is a **superkey** of _R_ if values of _K_ are **sufficient to identify a unique tuple** of each possible relation _r(R)_
  - _K_ is a **candidate key** of _R_ if _K_ is **minimal**
  - **Primary key** is a candidate key chosen as the principal means of identifying tuples within a relation
    - Should choose an attribute that **never or rarely changes**

        Superkey > Candidate Key > Primary Key

#### Foreign Keys (外键)

- A **foreign key** is an attribute that corresponds to **the primary key of _another relation_**

### Query Languages

- Languages used for user to request information from the database
- Categories of languages
  - Procedural
  - Non-procedural (declarative) (e.g. SQL)

## Fundamental Relational-Algebra-Operations

### Rational Algebra

- Six basic operators:
  - **Select**: ![Sigma](https://latex.codecogs.com/svg.latex?\sigma)
  - **Project**: ![Capital Pi](https://latex.codecogs.com/svg.latex?\Pi)
  - **Union**: ![Cup](https://latex.codecogs.com/svg.latex?\cup)
  - **Set Difference**: ![Minus](https://latex.codecogs.com/svg.latex?-)
  - **Cartesian Product**: ![Times](https://latex.codecogs.com/svg.latex?\times)
  - **Rename**: ![Rho](https://latex.codecogs.com/svg.latex?\rho)

#### Select Operation

- Notation: ![sel-notation]
- Definition: ![sel-definition]
- _p_ is called as **selection predicate (选择谓词)**, a formula in propositional calculus consisting of **terms**, each terms is one of:
  - _\<attribute\> op \<attribute\> or \<constant\>_

[sel-notation]:   https://latex.codecogs.com/svg.latex?\sigma_p(r)
[sel-definition]: https://latex.codecogs.com/svg.latex?\sigma_p(r)=\{t|t\in{r}\text{~and~}p(t)\}

#### Project Operation

- Notation: ![proj-notation]
  - where _A1, A2_ are **attribute names** and _r_ is a **relation name**
- The result is defined as the relation of k columns obtained by erasing the columns that are not listed
- **Duplicate rows are removed from result**, since relations are sets

[proj-notation]: https://latex.codecogs.com/svg.latex?\Pi_{A_1,A_2,\cdots,A_k}(r)

#### Union Operation

- Notation: ![union-notation]
- Definition: ![union-definition]
- For ![union-notation] to be valid:
  - _r, s_ must have the same **arity (元数)** (same number of attributes)
  - The attribute domains must be **compatible** (?)

[union-notation]:   https://latex.codecogs.com/svg.latex?{r}\cup{s}
[union-definition]: https://latex.codecogs.com/svg.latex?{r}\cup{s}=\{{t}\in{r}\text{~or~}{t}\in{s}\}

#### Set Difference Operation

- Notation: ![setdiff-notation]
- Definition: ![setdiff-definition]
- Set differences must be taken between compatible relations.
  - _r_ and _s_ must have the same arity
  - attribute domains of r and s must be compatible

[setdiff-notation]:   https://latex.codecogs.com/svg.latex?{r}-{s}
[setdiff-definition]: https://latex.codecogs.com/svg.latex?{r}-{s}=\{t|{t}\in{r}\text{~and~}{t}\in{s}\}

#### Cartesian Product Operation

- Notation: ![cproduct-notation]
- Definition: ![cproduct-definition]
- Assume that attributes of _r(R)_ and _s(S)_ are **disjoint**
- If attributes of _r(R)_ and _s(S)_ are not disjoint, then renaming must be used

[cproduct-notation]:   https://latex.codecogs.com/svg.latex?{r}\times{s}
[cproduct-definition]: https://latex.codecogs.com/svg.latex?{r}\times{s}=\{tq|{t}\in{r}\text{~and~}{q}\in{s}\}

#### Rename Operation

- Notation: ![rename-notation]
- Allows us to name, and therefore to refer to, the results of relational-algebra expressions
  - Returns the **expression _E_ under the name _x_**

[rename-notation]: https://latex.codecogs.com/svg.latex?{\rho}_x(E)

## Additional Relational-Algebra-Operations

### Natural Join Operation

- Notation: ![natural-join-notation]
- The result is:
  - Consider each pair of tuples _tr_ from _t_ and _ts_ from _s_,
  - If _tr_ has the same value as _ts_, add tuple _t_ to the result, where
    - _t_ has the same value as _tr_ on _r_
    - _t_ has the same value as _ts_ on _s_

[natural-join-notation]: https://latex.codecogs.com/svg.latex?\Join

### Divition Operation

- Notation: ![division-notation]

[divition-notation]: https://latex.codecogs.com/svg.latex?\div

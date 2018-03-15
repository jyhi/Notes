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

- **Select**
- **Project**
- **Union**
- **Set Difference**
- **Cartesian Product**
- **Rename**

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

- **Set Intersection**
- **Natural Join**
- **Division**
- **Assignment**

### Set Intersection Operation

- Notation: ![set-intersection-notation]
- Definition: ![set-intersection-definition]
- ![set-intersection-note]

[set-intersection-notation]: https://latex.codecogs.com/svg.latex?\cap
[set-intersection-definition]: https://latex.codecogs.com/svg.latex?{r}\cap{s}=\{t|{t}\in{r}\text{~and~}{t}\in{s}\}
[set-intersection-note]: https://latex.codecogs.com/svg.latex?{r}\cap{s}=r-(r-s)

### Natural Join Operation

- Notation: ![natural-join-notation]
- The result is:
  - Consider each pair of tuples _tr_ from _t_ and _ts_ from _s_,
  - If _tr_ has the same value as _ts_, add tuple _t_ to the result, where
    - _t_ has the same value as _tr_ on _r_
    - _t_ has the same value as _ts_ on _s_

[natural-join-notation]: https://latex.codecogs.com/svg.latex?\Join

### Division Operation

- Notation: ![division-notation]

[division-notation]: https://latex.codecogs.com/svg.latex?\div

### Assignment Operation

- Notation: ![assignment-notation]

[assignment-notation]: https://latex.codecogs.com/svg.latex?\leftarrow

## Extended Relational-Algebra-Operations

- **Generalized Projection**
- **Aggregate Functions**
- **Outer Join**

### Generalized Projection

- Notation: ![general-proj-notation]
  - _E_ is any relational-algebra expression
  - Each of _F1, F2, ..., Fn_ are arithmetic expressions involving constants and attributes in the schema of _E_

[general-proj-notation]: https://latex.codecogs.com/svg.latex?{\Pi}_{F_1,F_2,\cdots,F_n}(E)

### Aggregate Functions

- Aggregation function takes a collection of values and returns a single value as a result. **Duplicates are not eliminated.**
- Notation: ![aggregate-notation]
  - _E_ is any relational-algebra expression
  - _G1, G2, ..., Gn_ is a list of attributes on which to group (can be empty)
  - Each _Fi_ is an aggregate function
    - **avg**
    - **min**
    - **max**
    - **sum**
    - **count**
  - Each _Ai_ is an attribute name

[aggregate-notation]: https://latex.codecogs.com/svg.latex?_{G_1,G_2,\cdots,G_n}{\varrho}_{F_1(A_1),F_2(A_2),\cdots,F_n(A_n)}(E)

### Outer Join

- Notation:
  - Left Outer Join: <!-- ![left-outer-join-notation] -->
  - Right Outer Join: <!-- ![right-outer-join-notation] -->
  - Full Outer Join: <!-- ![full-outer-join-notation] -->

<!-- Help me... -->

<!-- [left-outer-join-notation]:  -->
<!-- [right-outer-join-notation]: -->
<!-- [full-outer-join-notation]:  -->

## Null Values

- Notation: _null_
- An unknown value
- **The result of any arithmetic exoression involving _null_ is _null_**
- **Aggregate functions simply ignore null values (as in SQL) _except count_**
- **Two _null_ s are considered the same (as in SQL)**

### Comparison

Comparisons with null values return the special truth value: _unknown_

- (_unknown_ OR _true_) = **_true_**
- (_unknown_ OR _false_) = _unknown_
- (_unknown_ OR _unknown_) = _unknown_
- (_unknown_ AND _true_) = _unknown_
- (_unknown_ AND _false_) = **_false_**
- (_unknown_ AND _unknown_) = _unknown_
- (NOT _unknown_) = _unknown_

In SQL **P is _unknown_** evaluates to **_true_** if predicate _P_ evaluates to _unknown_

Result of select predicate is treated as _false_ if evaluates to _unknown_

## Modification of The Database

- **Deletion**: ![deletion]
- **Insertion**: ![insertion]
- **Updating** ![updating]

[deletion]: https://latex.codecogs.com/svg.latex?{r}\leftarrow{r-E}
[insertion]: https://latex.codecogs.com/svg.latex?{r}\leftarrow{r}\cup{E}
[updating]: https://latex.codecogs.com/svg.latex?\Pi_{F_1,F_2,\cdots,F_n}(r)

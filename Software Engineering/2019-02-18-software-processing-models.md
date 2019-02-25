# Lecture 2: Software Processing Models

## Software Development Life Cycle

1. Requirement definition (specification)
  - understand and define **services**
  - identify **constraints**
2. Design and implementation
  - **convert** specifications to executable systems
3. Verification and validation (V&V testing)
  - (**verification**) check if a system **conforms to its specification**...
  - (**validation**) ... and **meets the customer's expectation**
4. Evolution
  - meet required **changes** from customers
  - and **bug corrections**

## Software Process and Process Model

- A **software process** is a set of activities, whose goal is the **development** or **evolution** of software
- A **software process model** is a **simplified representation** of a _software process_ from a specific perspective

## Process Models

- Waterfall
- Incremental
- Prototype
- Spiral
- Formal methods
  - Vienna Development Method (VDM)
  - The B method
  - _seldom used_

### The Waterfall Model

1. Analysis
  - _produces_ software specs
2. Design
  - _produces_ software arch
3. Coding
  - _produces_ source code
4. Test
  - _produces_ test reports
5. Maintenance
  - _produces_ maintenance records

Advantages:

- Straightforward
- Disciplined

Arguments:

- Users cannot describe requirements clearly at the beginning
- Hard to follow
- Projects using this model are often delayed

### Incremental Development

- Clients do **not** need to specify requirements for _the whole system_ at the beginning
  - Instead, specify _most important parts_
- A number of increments are defined

Process:

1. **Define** outline requirement
2. **Assign** requirements to _increments_
3. **Design** system architecture
4. **Develop** system _increment_
5. **Validate** _increment_
6. **Integrate** _increment_
7. **Validate** system
8. `goto 4.`

Advantages:

- Risk of failure is lower (compared to waterfall)
- Shorten delivery time

Disadvantages:

- System structure is _loose_
- Hard to define _increments_

### The Prototyping Model

1. Quick design
2. Identify software requirements
3. `goto 1.` -> refined prototypes

Advantages:

- Users can see initial look of a system
- Developers can have a quick design
- Prototypes can be developed further into a system

Arguments:

- Rushed
- Hard to ensure quality and to maintain

### The Spiral Model

An iterative software process model comining both _waterfall_ and _prototyping_.

![Spiral Model (Bohem)](./img/spiral-model-bohem.png)

![Spiral Model (A Variant)](./img/spiral-model-variant.png)

Advantages:

- Developers can use prototyping in _each_ evolution level
- Reducing risks

Arguments:

- Continual risk analysis
- Documents maintenance

# Lecture 4: System Models

**System models** are used to describe:

- **Environment**
  - context model, use case diagram, ...
- **Behavior flow**
  - state machine model, dataflow model, ...
- **Structure**
  - data models, object models, ...

... of a system.

## Context Models (上下文模型)

- Deciding **boundaries** of enviroment of a system
  - what are _not included in_ but _related with_ the system

## Use Case

A **use case** can be described in a _natural language_ text containing:

- **abstract** information (**initial description**),
- _or_ **refined** details (**concrete information**).

### Initial Description

At least the following 3 parts:

- **Name** of the use case
- Participation **actors**
- **Description**

### Concrete Information

- **Name** of the use case
- Use case **ID**
- Participation **actors**
- **Entry condition(s)**
- **_Scenario_**
- **Priority**
- **Exit condition(s)**
- Quality requirements
- Source
- ...

## Prioritize Use Case

- Support **major** business process
- Architectural **significance**
- Use of **new technologies**
- Needs of **susbtaintial** (large amount of) **research efforts**
- Great **improvement in efficiency**

## Use Case Diagrams

- Describing a system's functionalities **from the point of view of users (externally visible)**
  - **actors**: **role** of the user
  - **use cases** (interactors): **tasks** the system can perform
- First step in requirement specification
  - **must be determined by consulting the client**

Use cases should **focus on _goals_** rather than _processes_. Good use cases should be:

- **observable**
- **basic**

### Relationships in Use Case Diagrams

- Between _actors_ and _use cases_:
  - **"Communication"**
- Between _use cases_:
  - **"Include"**
    - _dashline with forward arrow_ (A -- include -> B)
    - some use cases that **share common parts**
      - e.g. authentication
  - **"Extend"**
    - _dashline with forward arrow_ (A -- extend -> B)
    - some use cases that **can be applied** to other ones
      - e.g. exception handling
  - **"Inheritance"**
    - _dashline with backward empty arrow_ (A \<|-- B)
      - but can be in any direction based on precedence
    - some use cases that **share a superset** use case
      - e.g. display book info... in HTML... in plain text

## Use Case Scenario

- A concrete **sequence of events**
- Occurs during one **particular execution path** in a _user case_
- For every _user case_, there is a _scenario_ that can describe the possible interactions between the user and the system for the _user case_
- **Basic scenario:**
  - normal sequence of events
  - achieving main goals of the use case without problem
  - _e.g. open-display-input-search-result of book searching machine_
- **Alternative scenario:**
  - something happening?
  - main goals cannot be achieved
  - normal cases cannot be achieved
  - _e.g. open-display-input-search-**nothing** of book searching machine_

## Behavior Models

Describing overall function of the system:

- State machine model (Finite State Machine)
  - event-driven, e.g. embedded systems
- Data flow model
  - data-driven, e.g. information systems

### State Machine Model

#### Elements in a State Machine Model

- **State** (necessary)
  - a mode of behavior, lasts for a period of time
- **Event** (necessary)
  - causes transition from a state to another
- **Action** (optional)
  - the behavior that the system reacts to an event
- **Condition** (optional)
  - a condition for an action to an event (?)

```
+---------+   Event [Condition] / Action    +---------+
| State 1 | ------------------------------> | State 2 |
+---------+                                 +---------+
```

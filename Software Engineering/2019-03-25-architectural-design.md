# Lecture 8: Architectural Design

- **Identify** subsystems
- **Establish** relationships between subsystems

## Subsystems

- Decomposite system into managable parts
- Each subsystem can be assigned to a developer or a team to implement independently
- Subsystems can be divided into simpler subsystems

## Design Fundamentals

- Abstraction
- Pattern
- Modularity
- Information hiding
- Independence
  - **Low coupling** between subsystems
  - **High cohesion** within a system
- Refinement
  - opposite to abstraction
- Refactoring

## Architecture In Different Perspectives

- **Static model**
  - Subsystems and components
- **Dynamic model**
  - Process in run-time
- **Interface model**
  - Services offered by each subsystem
- **Relationship model**
  - Calling relationships
- **Distribution model**
  - Distribution on different computers

## System Organization

- **Repository model**
  - Some attributes are shared among subsystems (e.g. API, security)
- **C/S model**
- **Layered model**
  - A layer can be changed with API being the same
    - performance can be a problem?

## Component Control

- **Centralized model**
  - Call-return model (tree structure)
  - Manager model (one component coordinates others)
- **Event-based model**
  - Broadcast model
  - Interrupt-driven model

# Lecture 3: Software Requirements

## Requirements

- Describe system **services** and **constraints**
- Very abstract or very detailed
- Used to
  - shown to contract biders
  - _validate_ the final system

### Services and Constraints

- **Services** are **functions** that a system should implement
  - e.g. show a menu, adjust font size, display a picture
- **Constraints** are **terms** that a system should follow
  - e.g. implement in C++, run on Windows XP, online

### Types of Requirements

- Readers
  - User requirements
  - System requirements
- Contents
  - Functional requirements
  - Non-functional requirements
  - Domain requirements (基于特定知识背景的需求)

#### Readers :: User Requirements

- Written **for customers** by either customers (themselves) or developers
- Usually in _natural languages_
  - _diagrams_ may be provided
- Specifying necessary **constraints**, _abstractly_

#### Readers :: System Requirements

- Written **for developers** by developers
- aka. System requirement specification
- Described in _structured_ documents (diagrams, tables, etc)
- Detailed descriptions of the system's functions, services and constraints, and **what should be implemented**

#### Contents :: Functional Requirements

- Describing **functionality** _or_ system **services**
  - functional user requirements: behaviors, I/O
  - functional system requirements: system services in detail

**Note:** Requirements can be imprecise:

- Ambiguous
- Incomplete
- Inconsistent

#### Contents :: Non-Functional Requirements

- Specifying system **properties** _and_ **constraints**
  - **Product** requirements
    - behaviors, like **performance, reliability, etc**
  - **Organizational** requirements
    - policies and procedures, like **process standard, implementation requirements, etc**
  - **External** requirements
    - not part of the system:
      - interoperability
      - privacy
      - security
      - ethics

It is hard to specify non-functional requirements:

- Try to specify requirements **quantatively, not qualitative**
- _Metrics:_
  - speed: second
  - size: MB, LOC
  - ease of use: hours, FPS
  - reliability: mean time to failure (MTTF)
  - robustness: %
  - portability: number (of targets)

#### Contents :: Domain Requirements

- Chacteristics of the application domain of system
- Problems:
  - no common backgrounds for customers or developers
  - confusion with functional requirements may happen
  - _difference in profession makes one feel words apart (隔行如泰山)_

### Requirement _Specification_

Specify users' requirements in a document, using either:

- (Structured) natural language
- Formal language
- Diagrams
- Tables

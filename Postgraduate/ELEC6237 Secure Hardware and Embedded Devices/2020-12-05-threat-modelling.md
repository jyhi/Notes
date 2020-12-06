# Threat Modelling

> "... process to identify, enumerate and prioritize potential threats."

Threat modelling should take place in the early stages of product development cycle, with detailed documentation of potential threats be the output of it.

## Threat Modelling Cycle

- Model
  - use a data flow diagram on how data enter and leave each system component
    - also shows system processes and trust boundaries
    - **external entity - rectangle**
    - **data flow - solid arrow**
    - **trust boundary - dashed line**
    - **process - circle**
    - **data storage - solid double line**
- Identify Threats
  - **_STRIDE_:** threats - properties
    - **Spoofing (冒用)** - authentication
    - **Tampering (篡改)** - integrity
    - **Repudiation (抵赖)** - non-repudiation
    - **Information Disclosure** - confidentiality
    - **Denial of Service** - availability
    - **Elevation of Privilege** - authorisation
- Migigate
  - one of the following is applied to each identified threats:
    - **use** standard defences and countermeasures
    - **develop** new defence mechanisms (hard and takes a long time)
    - **re-design** the product to eliminate the threat
    - **ignore**
- Validate

## Before Starting...

- Determine the **key threat scenarios** applicable
- Develop a number of **use cases**
- Define **external entities** and verify any assumptions made about them
- Identify **assets** and **security objectives** one want to achieve
  - assets:
    - resources and data saved
    - sensors, system components (e.g. storage)
    - interfaces (e.g. debug interface)

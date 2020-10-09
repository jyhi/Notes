# Introduction Part 1 & 2

## IoT Security Issues

> https://owasp.org/www-project-internet-of-things-top-10/

- Insecure web interface
- Insufficient authentication / authorisation
- Insecure network services
- Lack of transport encryption
- Privacy concerns
- Insecure cloud interface
- Insecure mobile interface
- Insufficient security configurability
- Insecure software / firmware
- Poor physical security

## Kerckhoffs' Principle

> _A cryptosystem should be secure even if everything about the system, except the key, is public knowledge._
>
> -- Auguste Kerckhoffs

In other words: **avoid security through obscurity**.

## The Attack Surface

A combination of all the attacks that can be used against a system.

| Examples | Local | Remote |
|-|-|-|
| Hardware | power analysis | USB malware |
| Software | cyber-physical (e.g. Stuxnet) | RCE (e.g. Mirai) |

## Threat Modelling

A structured approach to threat identifying, quantifying, and addressing.

1. Document architecture
2. Identify assets
3. Identify threats
4. Define security objectives
5. Mitigate
6. Validate (prove; not easy)

## Basic Security Concepts

- **Confidentiality**
  - keeping data secret
- **Integrity**
  - may refer to **data integrity** or **origin integrity**
  - correctness and trustworthiness
- **Availability**
  - authorized access to data is ensured
- **Non-repudiation**
- **Authentication**

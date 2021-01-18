# Application Layer

## Domain Name System (DNS)

A system of names and addresses.

- Names are higher-level identifiers; addresses are lower-level identifiers
- **Resolution** is mapping a name to an address

### DNS Namespace

A hierarchical approach to name management.

#### Top-Level Domains (TLDs)

- Run by ICANN

### DNS Zones

A **zone** is a **contiguous portion of the namespace**.

- Basis for _distribution_
- Each zone has a nameserver to contact for information about it

### Address Resolution

1. Computer requests local name server to resolve
2. Local name server asks the _root name server_
3. Root returns the name server for _lower zones_
4. Continue down zones until name server can answer

### DNS Resource Records

- `SOA`: Start of authority with key zone parameters
- `A`: IPv4 address of a host
- `AAAA`: IPv6 address of a host
- `CNAME`: Canonical name of a host
- `MX`: Mail eXchanger for the domain
- `NS`: Name Server of domain or delegated subdomains

## Email Message Transfer

Often SMTP (Simple Mail Transfer Protocol).

- Human-readable text commands
- Submission to MTA (Mail Transfer Agent) via port 587
- MTA to MTA via port 25
- Other ports for final delivery (POP, IMAP)

Headers, SMTP commands: refer to the slides.

## The World Wide Web

Web pages are transferred over HTTP.

### Handling Files

- `Content-Type`

## Uniform Resource Locators (URLs)

Pages are named with URLs.

## HyperText Transfer Protocol (HTTP)

A request-response protocol running on top of TCP.

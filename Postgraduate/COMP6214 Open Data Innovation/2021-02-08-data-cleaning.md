# Data Cleaning

Data Cleaning is the process of starting with (semi-)raw data from one or more sources and maintain reliable quality for your applications.

Real-life data are often:

- Incomplete
- Inconsistent
- Out-of-context
- ...

It's important to keep a note of the changes while cleaning the data.

## Types of Error in Real-Life Data

- Syntactic: violation of domain constraints
- Semantic: discrepancies between values and the real one in real life

## Properties of Clean Data

### Information Completeness

- Closed World Assumption (CWA): assuming the database has all real-world entities except some missing ones
- Open World Assumption (OWA): assuming the database misses related entities too

### Data Currency

Timeliness; not out-of-date.

## Data Validation

- Consumers understand the data easier
- Programmers do less "defensive programming"
- Producers can precisely define and validate the output

## Tools

- Linter: CSVLint, JSONLint
  - for syntactic errors
- _OpenRefine_
- _Excel_, or other spreadsheets
- _Bespoke Scripts_

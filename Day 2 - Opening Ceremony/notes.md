# Where do great architectures come from ?
Speaker: Mary Poppendieck

Get the presentation, it was really interesting. 

Good architecture needs:
- Redundancy
- Localization 
- Resiliency

# Intellectual Control
Speaker: George Fairbank @ Google

They were able to ship every 2 weeks

1995:
- Reasoning (manual tests confirm reasoning)

2020:
- Wide blanket of tests (reasoning is less critical but still compatible)

## Kinds of control
Intellectual control (IC)

Run the code: no

Dijkstra
- Proofs
- Structured programming

Beyond proofs
- Types, patterns, ADTs, DBC, static analysis.

Statistical control (SC)
- Run the code: yes
- % of state space

**Testing numbs us to our loss of reasoning**

Once lost, IC is hard to recover
- Software must stay on top of complexity

Striving for IC lowers complexity:
- Stay within complexity budget (assumption: complexity builds over time)
- Seek simpler designs (assumption: Minds are limited)
- Simplify existing code (assumption: Problems have many solutions of varying complexity)

How can we keep intellectual control ?
- Keep IC high
    - Culture of good, simple design
    - Property-based testing
    - Model-based testing

- Low IC? Ask:
    - Does process promote IC ?
    - Who is rewarded for helping IC ?

# Axiom
Speaker: Mark Richards

See PDF

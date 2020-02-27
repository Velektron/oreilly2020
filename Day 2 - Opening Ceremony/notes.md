# Where do great architectures come from ?
*Speaker: Mary Poppendieck*

Good architecture needs:
- Redundancy
- Localization 
- Resiliency

Not a lot of note for this one, but the presentation was an overview of her career and how architecture evolved.

[Complete presentation](https://cdn.oreillystatic.com/en/assets/1/event/307/Where%20do%20great%20architectures%20come%20from_%20Presentation.pdf)

# Intellectual Control
*Speaker: George Fairbank @ Google*

How he used to ships every two weeks;

- In 1995: Reasoning (manual tests confirm reasoning)
- In 2020: Wide blanket of tests (reasoning is less critical but still compatible)

## Kinds of control
### Intellectual control (IC)
Dijkstra
- Proofs
- Structured programming

Beyond proofs
- Types, patterns, ADTs, DBC, static analysis.

### Statistical control (SC)
- Run the code: yes
- % of state space

**Testing numbs us to our loss of reasoning**

Striving for IC lowers complexity:
- Stay within complexity budget (assumption: complexity builds over time)
- Seek simpler designs (assumption: Minds are limited)
- Simplify existing code (assumption: Problems have many solutions of varying complexity)

### How can we keep intellectual control ?
- Keep IC high
    - Culture of good, simple design
    - Property-based testing
    - Model-based testing

- Low IC? Ask:
    - Does process promote IC ?
    - Who is rewarded for helping IC ?

[Complete presentation](https://cdn.oreillystatic.com/en/assets/1/event/307/Intellectual%20control%20Presentation.pptx)

# Axiom
Speaker: Mark Richards

[The complete presentation will do a much better job than I at explaining it](https://conferences.oreilly.com/software-architecture/sa-ny/public/schedule/detail/81584)

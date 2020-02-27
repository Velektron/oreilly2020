# Software meeting for architect
## Why you should use metrics
- They are the foundation of the crucial "verify/measure" node of CI loop
- Free tools like Sonargraph-Explorer provides a lot of metrics
- Automated measurement in CI allow you to discover harmful trends early enough
- You can enforce quality stadards by using metrics in quality gates

## Why metrics are underutilized
- Perceived lack of tools and knowledge about them
- Lack of knowledge about metrics and how to read them
- Often a single metric does not tell the whole story
- Who has time for this ?
- Metrics are most useful when they are used to trigger actions
- Intimidating choices, which metrics should I use

## Fitness function
### Metrics quantify how well you met your goals
- Without measuring you are blind.
- Trust is good - control is better
- What are the goals ?
    - Maintainability ?
    - Scalability ?
    - Performance ?
    - Evolvability ?
    - Testability ?
    - Many more "lities..."

- Priorize goals
    - Pick up 3-4 "lities" as your top goals
    - Maintainability should always be on e of the (unless you write code that will never change)
    - Define and quantify what is means to achieve a goal.
- Fitness function:
    - Define how well you achieved your goal
    - Can be based on
        - Code metrics derived from static analysis
        - Operational metrics
        - Production metrics
        - Manually collected metrics
    - Automation is recommended, but not always possible.
    - Here we focus on code metrics ?

Attributes of spaghetti code
- High coupling
- Lots of cyclic dependencies
- No clear separation of responsabilities e.g. features are spread all over the place
- 90% of systems suffer from this problem.
- Metrics to identify spaghetti code
    - Average component Dependency
    - Maintainability Level
    - rACD = ACD / nb of elements
    - NCCD: Normalized Cumulated Component Dependency

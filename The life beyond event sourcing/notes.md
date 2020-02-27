# Event sourcing
## Back to basics
Event-Driven:
    - Once a process is done a message is broadcasted to a broker where tool can subscribe+-

## Event sourcing
### How does it work ? 
- Events needs to be played in chronological order
- Events are immutable so no update 

### Events
- Ephemeral data-structures
- Design the model with the business. 
- Acces historical data become painless
- Composing services are now actionable
- Scaling with snapshots

## Why it's dangerous ?
- Events and not tables
- Visibility of data
- Reversing events
    - Add not set
    - There is significant consequence when the processing logic is inside a domain model.
        - The domain model may alter it's internal state
        - They may not be visible to the event object's processing. 
    - Apply from the past snapshot and replaying event stream.

- External updates
    - Deal with systems that follow this approach.
    - Deal with systems that don't follow this approach
        - Wrap any external system with a Gateway

- External Queries
    - Can you trust external historical data ?

- Code change
    - New features
    - Defect fixes
    - Temporal logic


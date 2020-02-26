# Event Storming
Best architecture for agile thinking is the one that is supporting fast way to evolve. 

An architect job should be to teach other how to do architecture.

## Orchestration
Orchestrative system tends to be declarative.
- issueInvoice()
- queueItemForShipping()
- emailCustomer()

They are inherently delicate with tight coupled relationship.

## Reactive System
Going from the orchestration to the reactive can be done by removing the intelligence of the flow of process.
They receive an event orderPlaced().

Book: Domain-Driven Design Distilled

- Collaborative : Business people and developers working together. 

The whole component preface is invalid. Contexts are differents (e.g. book for a store vs book for a warehouse)

Database: Monstruous, fat, ugly global variable. 

The domain is the architecture, if you draw a picture of the domain you have the architecture of the program.

One of the biggest mistake of architecture is designing the static component. 

- Short narrative (couple of sentences) that describes a user performing a domain process that results in a valuable outcome. 
- Every team should have everything requires to produce what is expected (e.g. ui with no ux on the team)
- Stop thinking that we are Netflix.

You don't write story, you capture them, you discover them, you don't talk to your stake holder. The only stakeholder that matters: your customer. Others provide constraints and done criteria.

## Event storming
leanpub.com/introducing_eventstorming

### Event
Something that happened in the business that your customers care about
- Order submitted
- Payment received
- Nightly reconciliation complete.

Arrange these message on a timeline.

Identify what causes the event or what do you do with that event. (threedots.tech)

Shopping list for event storming : https://holub.com/event-storming/

- Post-it: Events, Action, Rules, Questions (red for question), Human activity, external system (pink)

In an Agile world, the only management tool needed are stickers on a wall.

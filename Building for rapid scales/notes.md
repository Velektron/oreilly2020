# Building for rapid speaking a deep-dive into the new york time messaging system
Speaker: Katerina

## Why messaging is important ?
- 53 Newsletters
- 4.2 Billion email to subscribers
- Push notification:
    - 7 channels
    - 50 million devices

- Messaging is a great way to engage with our readers
- Communication works both ways (reader can select what he wants to receive)

## Messaging at the NYT ?
Two systems (legacy):
- Newsletters platform
    - On GCP / Go
- Push notifications
    - On AWS / PHP

New platform capabilities (Go + GCP):
- Subscribe users to producter
- Administer product, campaigns, audience, schedules and messages
- Send a campaign
- Reporting

Architecture is event driven.

Microservice:
- Admin: "Morning briefing has been scheduled for 6 am"
- Triggers an event to the queue
- Dispatcher receive the events (reads the audience, and sent it)
- Compile and send services that send it to everyone
- Reporting + Delivery logs

All the data is in big query.

### Why build it in-house?
- Control of our data and our users data
- Light Vendor lock-in
- Flexibility in developing new feature

(photo prise du systeme)
## Demand for a better system
Largest newletter had 2 millions subscribers, SLA to deliver: 10 minutes.
By the end of 2019, it grew up to 9 millions and SLA was still 10 minutes.

## Building for Rapid Scale
### Scale how we dispatch the audience
- Must know state : A campaign should not fail because of a DB failure.
- Must process all rows in 1 minutes
- Must retry to load if request fail

Campaign->Orhestrator->[Dspatcher1...DispatcherX]

How was the query adapted to dispatch: by subscription timestamp (time window)

Divide and Conquer : Looks for windows in time, keep splitting the number of rows until we get 500k rows per operator. Once that daterange is found, store it somewhere and query accordingly.

### Scale how we send messages
Newletters: Process 1 email/request
Push notification: Process batch of messages / requests

Throughput : Number of Instances * request/instance

## Performance
### Setup
Max number of devices / Users Id: 1 Millions
Numbers of Pub/Sub: 15 (1000req/sec)


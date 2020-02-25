# Practical Microservices
## Monolith vs Microservices
- Bubble game metaphor for the users table

## What defines are services ?
- Services are autonomous
    - No one asks them for anything (you ask database for things) 
    - They don't ask anyone else for things (otherwise they're dependant)
    - They are oblivious to the system

- They aren't web APIs
    - You wouldn't find an express server in a service
- They aren't datababses
    - They don't have an API, not a facing for a GET request.

## How do you get services to do things ?
### Commands and Events
Messages are organized into *streams* (e.g. video:12345-1, video:command-12345-1)

## Architecturing the event system in 7 steps
- Go forth and brainstorm!
- Define messages / states
- The Story board
- Identify inputs
- Identify outputs
- Draw Boundaries
- 

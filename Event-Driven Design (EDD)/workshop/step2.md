from: xstate.js.org/viz
 
 ```js

  // Available variables:
  // - Machine
  // - interpret
  // - assign
  // - send
  // - sendParent
  // - spawn
  // - raise
  // - actions
  // - XState (all XState exports)
  
  const fetchMachine = Machine({
    id: 'todo_item',
    initial: 'created',
    context: {
      retries: 0
    },
    states: {
      created: {
        on: {
          ASSIGN: 'assigned'
        }
      },
      assigned: {
        on: {
          STARTS: 'started'
        }
      },
      started:{
        on: {
          COMPLETION: 'completed',
          WONT_DO: 'unassigned'
        }
      },
      completed: {
        type: 'final'
      },
      unassigned: {
        on: {
          REASSIGNATION: 'assigned'
        }
      }
    }
  });
  ```
2026-02-25 10:00

Status: #done

Tags: #uvm #tlm
# UVM TLM Methods

All communication methods are provided by the TLM interface class.

## Method Summary Table

| Mode | Put Port | Get Port | Peek Port |
| :--- | :--- | :--- | :--- |
| **Blocking** | `put()` | `get()` | `peek()` |
| **Non-blocking** | `try_put()` <br> `can_put()` | `try_get()` <br> `can_get()` | `try_peek()` <br> `can_peek()` |

## Detailed Method Descriptions

| Method       | Description                                                                                                                           | Usage Example           |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------ | :---------------------- |
| **put**      | **Blocking**: Sends a transaction to another component. It blocks until the transaction is successfully accepted.                     | `.put(trans_item)`      |
| **try_put**  | **Non-blocking**: Attempts to send a transaction. Returns `1` if the target is ready to accept, otherwise returns `0`.                | `.try_put(trans_item)`  |
| **can_put**  | **Non-blocking**: Checks if the target is ready to accept a transaction without actually sending one. Returns `1` if ready.           | `.can_put()`            |
| **get**      | **Blocking**: Retrieves a transaction from another component. Blocks until the transaction is successfully retrieved.                 | `.get(trans_item)`      |
| **try_get**  | **Non-blocking**: Attempts to retrieve a transaction. Returns `1` if a transaction is available and retrieved, otherwise returns `0`. | `.try_get(trans_item)`  |
| **can_get**  | **Non-blocking**: Checks if a transaction is available to be retrieved without actually getting it. Returns `1` if available.         | `.can_get()`            |
| **peek**     | **Blocking**: Retrieves a transaction without consuming (removing) it. Blocks until a transaction is available.                       | `.peek(trans_item)`     |
| **try_peek** | **Non-blocking**: Attempts to peek at a transaction. Returns `1` if a transaction is available, otherwise returns `0`.                | `.try_peek(trans_item)` |
| **can_peek** | **Non-blocking**: Checks if a transaction is available for peeking. Returns `1` if available.                                         | `.can_peek()`           |
| **write**    | **Non-blocking (Analysis)**: Broadcasts a transaction to any number of subscribers/listeners.                                         | `.write(trans_item)`    |

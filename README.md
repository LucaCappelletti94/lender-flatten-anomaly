# lender-flatten-anomaly

Repo trying to understand weird behavior of Lenders

## How to reproduce

* Clone the repo
* Run `cargo run`

## What to expect

The script will printout the following, where in this case `102491716180704` is the address of the stack vector.
For reasons currently unknown, the stack is not empty at the start of the SECOND parent loop, even though it has
been popped empty in the child loop.

```bash
Pushing row 0 to stack at address 8
Stack at address 102491716180704 after push: [0]
Popping row 0 from stack at address 102491716180704
Stack at address 102491716180704 before pop: [0]
Stack at address 102491716180704 after pop: []

thread 'main' panicked at src/main.rs:88:13:
Stack at address 102491716180704 should be empty at the start of the circuit search, but in parent is [0]
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```

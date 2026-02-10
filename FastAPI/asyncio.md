`Asyncio` is a Python Library used for concurrent programming including the use of async iterator in Python.
Its concurrency not multithreading.

- `asyncio` uses **cooperative multitasking**, not preemptive multitasking.
    
- This means **all tasks run in a single thread**, but **the code voluntarily yields control** at `await` points.

## 1. Running event loop

###  What is cooperative multitasking and preemptive multitasking


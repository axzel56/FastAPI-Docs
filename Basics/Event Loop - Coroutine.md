
## The Call Stack

- one thread == one call stack == one ting at a time

When a `webapi` is done, then it gets pushed into the task queue.


Event Loop task is to look at the the stack and look at the task queue, if the stack is empty, it takes the first thing on the task queue, that pushes it to the stack and gets run.

How it works.

- - The server creates coroutine tasks and registers them with the event loop.
- The event loop executes a coroutine until it hits `await`.
- At `await`, the coroutine yields control, and the event loop registers the I/O operation with the OS.
- The OS monitors the I/O and notifies the event loop when it is ready.
- The event loop resumes the paused coroutine.
# Why not use Multithread
Python(`CPython`) has things like `Global Interpreter Lock (GIL)`.

It allows:
- `Only ONE thread to execute Python bytecode at a time.`

# Coroutine

Coroutines are computer program components that generalize subroutines for non-preemptive multitasking by allowing execution to be suspended and resumed.
(a variant of functions that enables concurrency via cooperative multitasking)

When we use `async def`. Python does not execute it immediately. It returns a coroutine object.

```python
@app.get("/")
async def read_data():
	await asyncio.sleep(2)
	return {"ok": "xyz"}
```

`read_data` is a coroutine.

Flow:
1. Request comes in
2. FastAPI schedules the coroutine in event loop
3. When it hits `await`, it pauses.
4. Event loop runs other coroutines
5. When ready it results

##  Coroutines

- Run inside a single thread
    
- NOT managed by OS
    
- Managed by program itself (event loop)
    
- Cooperative multitasking
    

Important difference:

> OS switches threads automatically  
> Coroutines switch voluntarily at `await`
# Cooperative Multitasking

More threads = more context switching
Cooperative Multitasking: Switching between tasks only when a task is waiting for external resources.
It depends on task being polite and cooperative between all other task.

Concept: Each task either needs to complete or explicitly yield control to other task before other task can execute.

# Round Robin:
Its a preemptive scheduling technique used in OS and Networking to provide fair CPU access to all processes.
It assigns a fixed, equal time slice- time quantunm to each task in a circular, FIFO order

**How It Works:**

1. All processes enter a queue.
2. The scheduler picks the first process and executes it for the time quantum.
3. If the process finishes, it leaves the system.
4. If not, it moves to the end of the queue, and the next process starts.
5. This repeats until all processes are complete.

![[Pasted image 20260215213731.png]]
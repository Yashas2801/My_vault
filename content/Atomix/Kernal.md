# GPU Kernel

In the context of GPU computing, a **kernel** is a **small program or function that runs on the GPU** to perform the actual parallel work.

## Very simple idea

* **CPU/Host** = Manager
* **Kernel** = Job instructions
* **GPU** = Many workers doing the same job on lots of data

So when the application says “launch a kernel,” it means:

> “Start this GPU function on many threads in parallel.”

The verification strategy document also describes kernel launch this way: the application provides the **kernel function**, **grid dimensions**, **block dimensions**, and **kernel arguments**, and then the runtime/driver stack turns that into GPU work. 

## Example intuition

Suppose you want to add two arrays:

```c
C[i] = A[i] + B[i]
```

Instead of the CPU doing one element at a time, you write a **kernel** that says:

> “For each index `i`, add `A[i]` and `B[i]`, and store it in `C[i]`.”

Then the GPU runs that same kernel across many threads at once.

So:
* The **kernel code** is one function.
* The GPU runs **many copies of it in parallel**.
* Each thread handles a different piece of data.

## flow

* The **application** invokes a kernel.
* The **runtime + driver** package it.
* The **driver** builds a command buffer.
* The **GPU** executes it asynchronously. 

So the kernel is the **actual compute work** that gets launched on the GPU.

## Best one-line definition

> **A kernel is a GPU function that is launched from the host and executed in parallel by many GPU threads.**


> “Kernel means the piece of compute code that runs on the GPU. The host prepares the kernel launch, and the GPU executes many parallel threads of that kernel on the data.” 



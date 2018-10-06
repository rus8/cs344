Udacity cs344 Intro to Parallel Programming 
=====

## What is here 
My solutions for problems given in class.

Also I put some notes for myself in this readme.

System config:  
```
  OS:      Ubuntu 16.04 LTS  
  Kernel:  4.4.0-116-generic  
  CUDA:    9.0  
  GPU:     GeForce 840MX
```

## Notes

### Lecture 1
Core principles:
* Lot of simple compute units
* Parallel programming model
* Optimize for throughput not latency

CUDA programming model:
* Host-device paradigm
* Host allocates mem on device, copies data in both directions, and launches kernels
* Launch configuration parameters specify how many threads run in a block, and how many blocks to run `kernel<<<grid_size, block_size>>>`
___
### Lecture 2
Communication Paterns:
* Map (one-to-one)
* Gather (many-to-one)
* Scatter (one-to-many), calculate where to write
* Stencil (several-to-one), update each element in an array using it's neighbours with a pattern
* Transpose (one-to-one), matrix, array of structs -> struct of arrays

Memory model:
* Speed: Local (thread) > Shared (block) > Global (any thread) 
* Coalesced global memory access - successive threads read continious global memory locations faster

Programming details:
- GPU assigns Blocks to SM. 
- Block is on the one SM, so are it's threads. They have access to shared memory, which is allocated on SM.
- Block is finished, when all threads are finished. Kernel is finished, when all Blocks are finished.
- Always maximize (math/memory)

Syncronization. 
* `__syncthreads()` - barrier
* Atomic operations
___
### Lecture 3

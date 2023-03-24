# MicroPython C++ Memory Manager

This proof-of-concept MicroPython module is intended for use with the RP2 port of MicroPython.

It disables the `new`/`delete` overrides in Pico SDK and replaces them with its own implementations.

These are backed by a very crude, non-freeing memory allocator which throws a MicroPython exception on fail.

It includes a module `cppmem` which can be imported to see alloc/free statistics, and currently used memory.

It uses a fixed-size heap pool, causing MicroPython to scale its heap accordingly.

## MicroPython Module

```python
import cppmem
>>> cppmem.alloc_bytes()
10240
>>> cppmem.alloc_count()
451
>>> cppmem.free_count()
51
```

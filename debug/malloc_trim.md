#	--malloc_trim

##	Description
Run the `malloc_trim` system call. This operation attempts to release free memory from the heap (memory allocated by `malloc`) back to the operating system, potentially reducing the memory footprint of the process.

##  Arguments (optional)
This command takes no arguments.

##  Example usage
```
example_com:velocli> debug --malloc_trim

example_com:velocli>
```
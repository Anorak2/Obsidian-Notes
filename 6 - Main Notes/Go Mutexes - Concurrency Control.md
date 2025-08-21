
2024-12-28

Status:

Tags: [[Programming]] [[Golang]]
# Go Mutexes - Concurrency Control

Mutexes are a way inside of Go to handle problems that show up due to multiple routines accessing the same data, and this is a way to implement the classic types of locking from database.
```
import("symc")

type Board struct{
	mu sync.Mutex
	mboard [16][32]bool
	board_as_string string
}

...

	board.mu.Lock()
	board.mu.Unlock()
```

This is a very simple way to lock a structure so that only one thing can access it at a given time. 

# References
[[Locking]]

[[Concurrency Control]]

[[High Level Synchronization Control]]
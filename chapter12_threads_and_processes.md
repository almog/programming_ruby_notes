#Multithreading
- Let's implement the first fiber example with an enumerator.
- Coroutines using fibers
- Continuation
- Everything that's outside the Thread's block is potentially shared
- Thread#initialize's block can take any number of parameter
- Puts is not atomic - it splits it works into writing the input string and then writing a newline, that's why print should be considered when using threads.
- All threads are killed when a program is terminated, unless it sends a `join` message, with an optional timeout (the default is infinity).

## Manipulating Threads
- Thread#value, Thread#status, Thread#alive?, Thread#priority
- Thread.current is a way for a thread to reference itself. Does it have any other usages?
- Thread.list

## Thread variables
- Thread object can share data with the main thread or other threads by treating itself as a hash.


##Threads and Exceptions
- If the abort_on_exception = true flag or $DEBUG = true (`ruby -d`), then therads' exceptions are raised to the main thread.
- Otherwise, thread exceptions are remain silent until they'er joined.

##Mutual exclusion
- In the explanation for the sum not getting to 100,000, it's said that it's waiting to I/O at 100,000, but isn't I/O only ocurring when new_value % 250,000 == 0?
- Mutex#synchronize takes a block that wraps around Mutex#lock and Mutex#unlock (it follows a pattern similar to File.open)
- Mutex#try_locks tries to lock a mutex and return `false` if it can't (while Mutex#lock will wait for the Mutex object to get unlocked, potentially forever).
- What resources does a mutex lock? Everything in the current binding?
- The following two code examples are equivalent way of locking a resource for a short period of time:

```
loop do
  sleep 3600
  rate_mutex.synchronize do
    exchange_rates.update_from_online_feed
  end
end
```

```
rate_mutex.lock
loop do
  rate_mutex.sleep 3600
  exchange_rates.update_from_online_feed
end
```
## Queues

#Running Multiple Processes
- Object#system - writes the commands output to STDOUT, returns true for success, error if the command could not be found and false if the command returned an error (which can be found with $?).
- Backquotes returns the command STDOUT (but not STDERR)

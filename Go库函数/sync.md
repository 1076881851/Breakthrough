Go 语言的 `sync` 包提供了基本的同步原语，如互斥锁、条件变量、读写锁等，用于处理多协程间的同步问题。以下是 `sync` 包中一些常用的类型和它们的用法：

### 1. `sync.Mutex`
- **用途**：用于提供一种锁机制，以保护临界区，确保在同一时间只有一个协程可以执行临界区代码。
- **常用方法**：
  - `Lock()`：锁定 `Mutex`。如果锁已被其他协程持有，则调用协程将阻塞直到锁被释放。
  - `Unlock()`：解锁 `Mutex`。释放锁以供其他协程使用。

```go
var mu sync.Mutex
var count int

func increment() {
    mu.Lock()
    defer mu.Unlock()
    count++
}
```

### 2. `sync.RWMutex`
- **用途**：读写锁允许多个读操作同时进行，但写操作会完全独占锁。
- **常用方法**：
  - `RLock()`：为读操作锁定 `RWMutex`。
  - `RUnlock()`：释放读锁。
  - `Lock()`：为写操作锁定 `RWMutex`。
  - `Unlock()`：释放写锁。

```go
var rwMu sync.RWMutex
var data int

func readData() int {
    rwMu.RLock()
    defer rwMu.RUnlock()
    return data
}

func writeData(d int) {
    rwMu.Lock()
    defer rwMu.Unlock()
    data = d
}
```

### 3. `sync.WaitGroup`
- **用途**：用于等待一组协程的完成。
- **常用方法**：
  - `Add(delta int)`：设置等待协程的数量。
  - `Done()`：每个协程在完成时调用，相当于 `Add(-1)`。
  - `Wait()`：阻塞调用协程，直到所有协程完成。

```go
var wg sync.WaitGroup

func worker(id int) {
    defer wg.Done()
    fmt.Println("Worker", id, "done")
}

func main() {
    for i := 1; i <= 5; i++ {
        wg.Add(1)
        go worker(i)
    }
    wg.Wait()
    fmt.Println("All workers done")
}
```

### 4. `sync.Once`
- **用途**：确保某个操作在多协程环境下只执行一次。
- **常用方法**：
  - `Do(f func())`：执行传入的函数 `f`，并确保无论多少协程调用 `Do`，函数 `f` 只会被执行一次。

```go
var once sync.Once
var initConfig func()

func setup() {
    once.Do(initConfig)
}
```

### 5. `sync.Cond`
- **用途**：条件变量，用于等待或宣布事件的发生。
- **常用方法**：
  - `NewCond(*Mutex)`：创建一个新的 `Cond`。
  - `Wait()`：等待条件变量的通知。
  - `Signal()`：唤醒一个等待 `Cond` 的协程。
  - `Broadcast()`：唤醒所有等待 `Cond` 的协程。

```go
var mu sync.Mutex
var cond = sync.NewCond(&mu)
var ready bool

func process() {
    mu.Lock()
    for !ready {
        cond.Wait()
    }
    fmt.Println("Processing")
    mu.Unlock()
}

func makeReady() {
    mu.Lock()
    ready = true
    cond.Broadcast()
    mu.Unlock()
}
```

以上是 `sync` 包中一些常用的类型和方法。这些同步原语在处理并发问题时非常有用，尤其是在设计需要多协程协作的复杂系统时。

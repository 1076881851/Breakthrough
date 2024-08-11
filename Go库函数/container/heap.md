Go 语言的 `container/heap` 包提供了一个接口和实现，可以使任何类型的切片作为最小堆进行操作。这个包非常适合解决需要快速访问最小元素（或通过小修改，最大元素）的问题，如优先队列的实现。使用这个包需要实现 `heap.Interface`，它包括 `sort.Interface` 的所有方法以及 `Push` 和 `Pop` 方法。

### `heap.Interface` 方法
要使用 `container/heap` 包，你的类型需要实现以下方法：

1. **`Len() int`**
   - 返回堆中的元素数量。

2. **`Less(i, j int) bool`**
   - 报告索引 `i` 的元素是否应该排在索引 `j` 的元素之前。对于最小堆，这意味着元素 `i` 应该小于元素 `j`。

3. **`Swap(i, j int)`**
   - 交换索引 `i` 和 `j` 的元素。

4. **`Push(x interface{})`**
   - 向堆中添加元素 `x`。`Push` 方法不直接调用，而是通过 `heap.Push` 调用。

5. **`Pop() interface{}`**
   - 从堆中移除并返回最小元素（根据 `Less` 方法定义）。`Pop` 方法不直接调用，而是通过 `heap.Pop` 调用。

### `container/heap` 包的函数
以下是一些在 `container/heap` 包中可用的函数，这些函数操作实现了 `heap.Interface` 的任何类型：

1. **`heap.Init(h Interface)`**
   - 对切片 `h` 进行堆初始化。这个操作建立堆的不变性，是任何后续堆操作之前必需的。
   - 示例：
     ```go
     h := &IntHeap{2, 1, 5}
     heap.Init(h)
     ```

2. **`heap.Push(h Interface, x interface{})`**
   - 向堆 `h` 添加元素 `x`。`Push` 之后，通常需要调用 `heap.Init` 来重新确保堆的不变性。
   - 示例：
     ```go
     heap.Push(h, 3)
     ```

3. **`heap.Pop(h Interface) interface{}`**
   - 从堆 `h` 移除并返回堆顶元素（该元素是最小的）。使用后，堆的不变性仍然保持。
   - 示例：
     ```go
     min := heap.Pop(h) // min 是 int 类型
     ```

4. **`heap.Remove(h Interface, i int) interface{}`**
   - 移除并返回位于索引 `i` 的元素。
   - 示例：
     ```go
     removedElement := heap.Remove(h, 1)
     ```

5. **`heap.Fix(h Interface, i int)`**
   - 修改位置 `i` 的元素后，调整堆以保持堆的不变性。
   - 示例：
     ```go
     (*h)[0] = 10
     heap.Fix(h, 0)
     ```

### 示例：实现一个最小堆
```go
package main

import (
    "container/heap"
    "fmt"
)

type IntHeap []int

func (h IntHeap) Len() int           { return len(h) }
func (h IntHeap) Less(i, j int) bool { return h[i] < h[j] }
func (h IntHeap) Swap(i, j int)      { h[i], h[j] = h[j], h[i] }

func (h *IntHeap) Push(x interface{}) {
    *h = append(*h, x.(int))
}

func (h *IntHeap) Pop() interface{} {
    old := *h
    n := len(old)
    x := old[n-1]
    *h = old[0 : n-1]
    return x
}

func main() {
    h := &IntHeap{2, 1, 5}
    heap.Init(h)
    heap.Push(h, 3)
    fmt.Printf("minimum: %d\n", (*h)[0])
    for h.Len() > 0 {
        fmt.Printf("%d ", heap.Pop(h))
    }
}
```

这个示例展示了如何定义一个最小堆、初始化、添加元素、并从中移除所有元素。使用 `container/heap` 包可以有效地管理数据集合，特别是在需要快速访问集合中最小或最大元素的场景中。

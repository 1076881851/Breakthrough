Go 语言的 `container/list` 包提供了一个实现双向链表的库。这个包中的 `List` 类型代表整个链表，而 `Element` 类型代表链表中的每一个元素。这种结构特别适用于需要频繁插入和删除元素的场景，例如实现队列和栈。

### `List` 类型的方法
以下是 `container/list` 包中 `List` 类型的一些常用方法及其用法：

1. **`Init() *List`**
   - 初始化或清空链表。
   - 示例：
     ```go
     var myList list.List
     myList.Init()
     ```

2. **`Len() int`**
   - 返回链表中的元素数量。
   - 示例：
     ```go
     fmt.Println(myList.Len()) // 输出链表长度
     ```

3. **`Front() *Element`**
   - 返回链表的第一个元素。
   - 示例：
     ```go
     firstElement := myList.Front()
     ```

4. **`Back() *Element`**
   - 返回链表的最后一个元素。
   - 示例：
     ```go
     lastElement := myList.Back()
     ```

5. **`PushFront(v interface{}) *Element`**
   - 在链表的前端插入一个新元素，并返回该元素。
   - 示例：
     ```go
     myList.PushFront(1)
     ```

6. **`PushBack(v interface{}) *Element`**
   - 在链表的后端插入一个新元素，并返回该元素。
   - 示例：
     ```go
     myList.PushBack(2)
     ```

7. **`InsertBefore(v interface{}, mark *Element) *Element`**
   - 在链表中的 `mark` 元素之前插入一个新元素，并返回该元素。
   - 示例：
     ```go
     myList.InsertBefore(0, myList.Front())
     ```

8. **`InsertAfter(v interface{}, mark *Element) *Element`**
   - 在链表中的 `mark` 元素之后插入一个新元素，并返回该元素。
   - 示例：
     ```go
     myList.InsertAfter(3, myList.Back())
     ```

9. **`Remove(e *Element) interface{}`**
   - 从链表中移除元素 `e` 并返回其值。
   - 示例：
     ```go
     element := myList.Front()
     removedValue := myList.Remove(element) // 移除第一个元素
     ```

### `Element` 类型的字段
`Element` 类型包含以下字段，可以用来访问元素的值和它在链表中的位置：

- **`Value interface{}`**
  - 存储在元素中的数据。
- **`Next() *Element`**
  - 返回链表中该元素的下一个元素。
- **`Prev() *Element`**
  - 返回链表中该元素的前一个元素。

### 示例：使用 `container/list`
下面是一个使用 `container/list` 包的简单示例，展示了如何创建一个链表，添加元素，以及遍历链表：

```go
package main

import (
    "container/list"
    "fmt"
)

func main() {
    myList := list.New()
    myList.PushBack("Hello")
    myList.PushFront("World")
    myList.InsertAfter("Go", myList.Back())

    for e := myList.Front(); e != nil; e = e.Next() {
        fmt.Println(e.Value)
    }
}
```

这个示例首先创建了一个新的链表，然后在链表的前端和后端添加了元素，并在最后一个元素后面插入了一个新元素。最后，它遍历链表并打印出每个元素的值。

`container/list` 的这些功能使其成为在需要动态数据结构时的一个强大工具，特别是当你需要频繁地在数据结构的中间部分插入或删除元素时。

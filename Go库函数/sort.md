Go 语言的 `sort` 包提供了一系列用于排序的函数和接口，这些工具可以帮助你对不同类型的数据进行排序。下面是 `sort` 包中一些常用函数的列表和它们的用法：

### 基本排序函数

1. **`sort.Ints(slice []int)`**
   - 对整数切片进行升序排序。
   - 示例：
     ```go
     nums := []int{5, 3, 4, 7, 2, 1, 9}
     sort.Ints(nums) // 升序排序
     ```

2. **`sort.Float64s(slice []float64)`**
   - 对浮点数切片进行升序排序。
   - 示例：
     ```go
     floats := []float64{3.1, 1.4, 2.8, 5.9}
     sort.Float64s(floats) // 升序排序
     ```

3. **`sort.Strings(slice []string)`**
   - 对字符串切片进行升序排序。
   - 示例：
     ```go
     strs := []string{"banana", "apple", "cherry"}
     sort.Strings(strs) // 升序排序
     ```

### 通用排序函数

4. **`sort.Slice(slice interface{}, less func(i, j int) bool)`**
   - 对任意类型的切片进行排序，需要提供一个比较元素大小的函数。
   - 示例：
     ```go
     people := []struct{Name string; Age int}{
         {"Alice", 30}, {"Bob", 25}, {"Clara", 28},
     }
     sort.Slice(people, func(i, j int) bool {
         return people[i].Age < people[j].Age // 根据年龄升序排序
     })
     ```

5. **`sort.SliceStable(slice interface{}, less func(i, j int) bool)`**
   - 类似于 `sort.Slice`，但保证排序稳定性，即相等元素的原始顺序不会改变。
   - 示例：
     ```go
     people := []struct{Name string; Age int}{
         {"Alice", 30}, {"Bob", 30}, {"Clara", 28},
     }
     sort.SliceStable(people, func(i, j int) bool {
         return people[i].Age < people[j].Age // 根据年龄升序排序
     })
     ```

### 辅助函数

6. **`sort.Reverse(data sort.Interface) sort.Interface`**
   - 返回一个新的 `sort.Interface`，该接口会逆转原有的 `Less` 方法，可以用于实现降序排序。
   - 示例：
     ```go
     nums := sort.IntSlice{5, 3, 4, 7, 2, 1, 9}
     sort.Sort(sort.Reverse(nums)) // 降序排序
     ```

7. **`sort.IsSorted(data sort.Interface) bool`**
   - 检查数据是否已经排序。
   - 示例：
     ```go
     nums := []int{1, 2, 3, 4}
     fmt.Println(sort.IntsAreSorted(nums)) // 输出：true
     ```

8. **`sort.SearchInts(a []int, x int) int`**
   - 在升序排序的整数切片中搜索元素，返回元素应该插入的位置以保持切片的排序。
   - 示例：
     ```go
     nums := []int{1, 2, 4, 6, 8}
     index := sort.SearchInts(nums, 5)
     fmt.Println(index) // 输出：3
     ```

### 总结

Go 的 `sort` 包提供了强大的工具集，可以处理各种排序需求。从基本的类型特定排序到更复杂的自定义排序，通过这些函数，你可以轻松实现高效和稳定的排序操作。这些工具的灵活性和简单性使得它们在 Go 程序中非常有用。

Go 语言的 `strings` 包提供了一系列用于操作 UTF-8 编码的字符串的函数。这些函数非常有用，尤其是在处理文本数据时。下面是 `strings` 包中一些常用函数的列表及其用法：

### 1. **`strings.Contains(s, substr string) bool`**
   - 检查字符串 `s` 是否包含子串 `substr`。
   - 示例：
     ```go
     fmt.Println(strings.Contains("hello world", "world")) // 输出：true
     ```

### 2. **`strings.Count(s, substr string) int`**
   - 返回子串 `substr` 在字符串 `s` 中的非重叠出现次数。
   - 示例：
     ```go
     fmt.Println(strings.Count("cheese", "e")) // 输出：3
     ```

### 3. **`strings.HasPrefix(s, prefix string) bool`**
   - 检查字符串 `s` 是否以 `prefix` 开头。
   - 示例：
     ```go
     fmt.Println(strings.HasPrefix("golang", "go")) // 输出：true
     ```

### 4. **`strings.HasSuffix(s, suffix string) bool`**
   - 检查字符串 `s` 是否以 `suffix` 结尾。
   - 示例：
     ```go
     fmt.Println(strings.HasSuffix("golang", "lang")) // 输出：true
     ```

### 5. **`strings.Index(s, substr string) int`**
   - 返回子串 `substr` 在字符串 `s` 中首次出现的索引，如果未找到则返回 -1。
   - 示例：
     ```go
     fmt.Println(strings.Index("chicken", "ken")) // 输出：4
     ```

### 6. **`strings.Join(a []string, sep string) string`**
   - 将字符串切片 `a` 使用分隔符 `sep` 连接成一个新的字符串。
   - 示例：
     ```go
     fmt.Println(strings.Join([]string{"hello", "world"}, " ")) // 输出："hello world"
     ```

### 7. **`strings.Repeat(s string, count int) string`**
   - 将字符串 `s` 重复 `count` 次。
   - 示例：
     ```go
     fmt.Println(strings.Repeat("na", 2)) // 输出："nana"
     ```

### 8. **`strings.Replace(s, old, new string, n int) string`**
   - 在字符串 `s` 中，将 `old` 替换为 `new`，最多替换 `n` 次。如果 `n` 为 -1，则替换所有匹配项。
   - 示例：
     ```go
     fmt.Println(strings.Replace("oink oink oink", "k", "ky", 2)) // 输出："oinky oinky oink"
     ```

### 9. **`strings.Split(s, sep string) []string`**
   - 根据分隔符 `sep` 将字符串 `s` 分割成多个子字符串，返回字符串切片。
   - 示例：
     ```go
     fmt.Println(strings.Split("a,b,c", ",")) // 输出：["a" "b" "c"]
     ```

### 10. **`strings.ToLower(s string) string`**
   - 将字符串 `s` 中的所有字符转换为小写。
   - 示例：
     ```go
     fmt.Println(strings.ToLower("GoLang")) // 输出："golang"
     ```

### 11. **`strings.ToUpper(s string) string`**
   - 将字符串 `s` 中的所有字符转换为大写。
   - 示例：
     ```go
     fmt.Println(strings.ToUpper("GoLang")) // 输出："GOLANG"
     ```

### 12. **`strings.TrimSpace(s string) string`**
   - 去除字符串 `s` 开头和结尾的空白符号。
   - 示例：
     ```go
     fmt.Println(strings.TrimSpace("  hello world  ")) // 输出："hello world"
     ```

### 13. **`strings.Trim(s, cutset string) string`**
   - 去除字符串 `s` 开头和结尾的包含在 `cutset` 中的任何字符。
   - 示例：
     ```go
     fmt.Println(strings.Trim("!!!Hello, Gophers!!!", "!")) // 输出："Hello, Gophers"
     ```

这些函数覆盖了字符串处理的大部分常见需求，从基本的搜索、替换到更复杂的操作如分割和连接等，都是在日常编程中非常有用的工具。

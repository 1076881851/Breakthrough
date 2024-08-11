Go 语言的 `strconv` 包提供了用于处理字符串与基本数据类型之间转换的函数。这些函数非常有用，尤其是在需要从字符串解析数字或将数字格式化为字符串的场景中。以下是 `strconv` 包中一些常用函数的列表及其用法：

### 字符串与整数之间的转换

1. **`strconv.Atoi(s string) (int, error)`**
   - 将字符串 `s` 转换为 `int` 类型。
   - 示例：
     ```go
     i, err := strconv.Atoi("123")
     if err != nil {
         fmt.Println(err)
     } else {
         fmt.Println(i) // 输出：123
     }
     ```

2. **`strconv.Itoa(i int) string`**
   - 将整数 `i` 转换为字符串。
   - 示例：
     ```go
     s := strconv.Itoa(123)
     fmt.Println(s) // 输出："123"
     ```

### 字符串与浮点数之间的转换

3. **`strconv.ParseFloat(s string, bitSize int) (float64, error)`**
   - 将字符串 `s` 转换为浮点数，`bitSize` 指定了精度（32 或 64 位）。
   - 示例：
     ```go
     f, err := strconv.ParseFloat("3.1415", 64)
     if err != nil {
         fmt.Println(err)
     } else {
         fmt.Println(f) // 输出：3.1415
     }
     ```

4. **`strconv.FormatFloat(f float64, fmt byte, prec, bitSize int) string`**
   - 将浮点数 `f` 格式化为字符串。`fmt` 字节可以是 'f'（无指数）、'e'（科学计数法）、'g'（根据情况选择 'e' 或 'f'），`prec` 指定精度。
   - 示例：
     ```go
     s := strconv.FormatFloat(3.1415, 'f', 2, 64)
     fmt.Println(s) // 输出："3.14"
     ```

### 字符串与布尔值之间的转换

5. **`strconv.ParseBool(str string) (bool, error)`**
   - 将字符串转换为布尔值。接受 "1", "t", "T", "true", "TRUE", "True" (为真)；"0", "f", "F", "false", "FALSE", "False" (为假)。
   - 示例：
     ```go
     b, err := strconv.ParseBool("true")
     if err != nil {
         fmt.Println(err)
     } else {
         fmt.Println(b) // 输出：true
     }
     ```

### 字符串与其他数字类型之间的转换

6. **`strconv.ParseInt(s string, base int, bitSize int) (int64, error)`**
   - 将字符串 `s` 转换为 `int64`，`base` 指定进制（如 10 表示十进制），`bitSize` 指定目标类型的位大小（如 32 或 64）。
   - 示例：
     ```go
     i, err := strconv.ParseInt("123", 10, 64)
     if err != nil {
         fmt.Println(err)
     } else {
         fmt.Println(i) // 输出：123
     }
     ```

7. **`strconv.FormatInt(i int64, base int) string`**
   - 将整数 `i` 格式化为 `base` 进制的字符串。
   - 示例：
     ```go
     s := strconv.FormatInt(123, 10)
     fmt.Println(s) // 输出："123"
     ```

8. **`strconv.ParseUint(s string, base int, bitSize int) (uint64, error)`**
   - 类似 `strconv.ParseInt`，但用于无符号整数。
   - 示例：
     ```go
     u, err := strconv.ParseUint("123", 10, 64)
     if err != nil {
         fmt.Println(err)
     } else {
         fmt.Println(u) // 输出：123
     }
     ```

### 其他实用函数

9. **`strconv.Quote(s string) string`**
   - 返回一个双引号围绕的字符串，必要时进行转义。
   - 示例：
     ```go
     q := strconv.Quote("Hello, world!")
     fmt.Println(q) // 输出："Hello, world!"
     ```

10. **`strconv.Unquote(s string) (string, error)`**
    - 将双引号围绕的字符串进行解析，并去除外围的双引号。
    - 示例：
      ```go
      original, err := strconv.Unquote("\"Hello, world!\"")
      if err != nil {
          fmt.Println(err)
      } else {
          fmt.Println(original) // 输出：Hello, world!
      }
      ```

这些函数是 `strconv` 包中的一部分，它们提供了强大的工具集，用于在字符串和其他基本类型之间进行转换。这些功能在处理文本数据和数值数据之间的转换时非常有用，特别是在解析配置文件、处理表单数据或进行数据序列化时。

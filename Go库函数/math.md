Go 语言的 `math` 包提供了丰富的数学常数和数学函数，用于处理各种数学计算。这些函数大多是对浮点数的操作。下面是 `math` 包中一些常用函数的列表和它们的用法：

### 数学常数

1. **`math.Pi`**
   - 圆周率的近似值。
   - 示例：
     ```go
     fmt.Println(math.Pi) // 输出圆周率的值
     ```

2. **`math.E`**
   - 自然对数的底数。
   - 示例：
     ```go
     fmt.Println(math.E) // 输出自然对数的底数
     ```

### 基础数学运算

3. **`math.Abs(x float64) float64`**
   - 返回 `x` 的绝对值。
   - 示例：
     ```go
     fmt.Println(math.Abs(-3.5)) // 输出 3.5
     ```

4. **`math.Sqrt(x float64) float64`**
   - 返回 `x` 的平方根。
   - 示例：
     ```go
     fmt.Println(math.Sqrt(16)) // 输出 4
     ```

5. **`math.Pow(x, y float64) float64`**
   - 返回 `x` 的 `y` 次方。
   - 示例：
     ```go
     fmt.Println(math.Pow(2, 3)) // 输出 8
     ```

6. **`math.Exp(x float64) float64`**
   - 返回 `e` 的 `x` 次幂。
   - 示例：
     ```go
     fmt.Println(math.Exp(1)) // 输出自然对数的底数 e
     ```

7. **`math.Log(x float64) float64`**
   - 返回 `x` 的自然对数。
   - 示例：
     ```go
     fmt.Println(math.Log(math.E)) // 输出 1
     ```

### 三角函数

8. **`math.Sin(x float64) float64`**
   - 返回角 `x`（弧度）的正弦值。
   - 示例：
     ```go
     fmt.Println(math.Sin(math.Pi / 2)) // 输出 1
     ```

9. **`math.Cos(x float64) float64`**
   - 返回角 `x`（弧度）的余弦值。
   - 示例：
     ```go
     fmt.Println(math.Cos(math.Pi)) // 输出 -1
     ```

10. **`math.Tan(x float64) float64`**
    - 返回角 `x`（弧度）的正切值。
    - 示例：
      ```go
      fmt.Println(math.Tan(math.Pi / 4)) // 输出 1
      ```

### 反三角函数

11. **`math.Asin(x float64) float64`**
    - 返回 `x` 的反正弦值，结果为弧度。
    - 示例：
      ```go
      fmt.Println(math.Asin(1)) // 输出 π/2
      ```

12. **`math.Acos(x float64) float64`**
    - 返回 `x` 的反余弦值，结果为弧度。
    - 示例：
      ```go
      fmt.Println(math.Acos(1)) // 输出 0
      ```

13. **`math.Atan(x float64) float64`**
    - 返回 `x` 的反正切值，结果为弧度。
    - 示例：
      ```go
      fmt.Println(math.Atan(1)) // 输出 π/4
      ```

### 舍入和取整函数

14. **`math.Floor(x float64) float64`**
    - 向下取整，返回不大于 `x` 的最大整数。
    - 示例：
      ```go
      fmt.Println(math.Floor(3.7)) // 输出 3
      ```

15. **`math.Ceil(x float64) float64`**
    - 向上取整，返回不小于 `x` 的最小整数。
    - 示例：
      ```go
      fmt.Println(math.Ceil(3.3)) // 输出 4
      ```

16. **`math.Round(x float64) float64`**
    - 四舍五入到最接近的整数。
    - 示例：
      ```go
      fmt.Println(math.Round(3.5)) // 输出 4
      fmt.Println(math.Round(3.49)) // 输出 3
      ```

### 其他有用的函数

17. **`math.Max(x, y float64) float64`**
    - 返回 `x` 和 `y` 中的最大值。
    - 示例：
      ```go
      fmt.Println(math.Max(3, 5)) // 输出 5
      ```

18. **`math.Min(x, y float64) float64`**
    - 返回 `x` 和 `y` 中的最小值。
    - 示例：
      ```go
      fmt.Println(math.Min(3, 5)) // 输出 3
      ```

这些函数是 `math` 包中最常用的一部分，涵盖了从基本的数学运算到更高级的函数。这个包是进行科学和工程计算时不可或缺的工具。

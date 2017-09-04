# 平时练习Go的代码

go实现递归：

```
package main

import "fmt"

func main() {
	var result = fibonacci(10)
	fmt.Printf("fibonacci(%d) is: %d\n", 10, result)

}

func fibonacci(n int) (res int) {
	if n <= 0 {
		res = 0
	}else {
		res = n + fibonacci(n-1)
	}
	return
}
```

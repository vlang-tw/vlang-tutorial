# 布林（Boolean）

布林表示了邏輯的真假值`true`及`false`：

```
success := false
fail := true
```

在定義函式參數及結構字段時使用關鍵字`bool來`表示布林資料型別。

邏輯運算會產生布林值的結果，以下是V程式語言的邏輯運算符：

* `&&`：邏輯AND，左右的運算元皆是`true`時評估為`true`
* `||`：邏輯OR，左右的運算元至少一個運算元是`true`評估為true
* `!`：邏輯NOT，運算元是false時評估為true，反之亦然。

範例：邏輯運算符`&&`

```v
module main

fn main() {
	w := true && true
	println('w: $w')
	x := false && true
	println('x: $x')
	y := true && false
	println('y: $y')
	z := false && false
	println('z: $z')
	/*
	w: true
	x: false
	y: false
	z: false
	*/
}
```

範例：邏輯運算符`||`

```v
module main

fn main() {
	w := true || true
	println('w: $w')
	x := false || true
	println('x: $x')
	y := true || false
	println('y: $y')
	z := false || false
	println('z: $z')
	/*
	w: true
	x: true
	y: true
	z: false
	*/
}
```

範例：邏輯運算符`!`

```v
module main

fn main() {
	x := true
	println('x: $x')
	y := !x
	println('y: $y')
	z := !y
	println('z: $z')
	/*
	x: true
	y: false
	z: true
	*/
}
```

邏輯運算的運算元皆為布林型別，而其他型別之間的關係評估可以使用關係運算符：

* 少於`<`：左側運算元的值小於右側運算元的值時為`true`
* 多於`>`：左側運算元的值大於右側運算元的值時為`true`
* 等於`==`：左側運算元的值與右側運算元的值相同時為`true`
* 不等於==：左側運算元的值與右側運算元的值不相同時為`true`
* 少於或等於`<=`：左側運算元的值小於或相同於右側運算元時為`true`
* 多於或等於`>=`：左側運算元的值大於或相同於右側運算元時為`true`

範例：關係運算符

```v
module main

fn main() {
	mut result := false
	mut my_coins := 1000
	mut friend_coins := 900
	println("I have $my_coins coins.")
	println("friend has $friend_coins coins.")

	// less than
	result = friend_coins < my_coins
	println("friend's less than mine: $result") // true
	
	// not equal to
	result = friend_coins != my_coins
	println("friend's not equal to mine: $result") // true

	// greater than
	println("I give friend 200 coins.")
	my_coins = my_coins - 200
	friend_coins = friend_coins + 200
	result = friend_coins > my_coins
	println("friend's greater than mine: $result") // true

	// equal to
	println("friend gives me 150 coins.")
	friend_coins = friend_coins - 150
	my_coins = my_coins + 150
	result = friend_coins == my_coins
	println("friend's equal to mine: $result") // true

	// less than or equal to
	println('my coins is less than or equal to 900: ${my_coins <= 900}') // false
	println('my coins is less than or equal to 950: ${my_coins <= 950}') // true
	println('my coins is less than or equal to 1000: ${my_coins <= 1000}') // true

	// greater than or equal to
	println('my coins is greater or equal to 900: ${my_coins >= 900}') // true
	println('my coins is greater or equal to 950: ${my_coins >= 950}') // true
	println('my coins is greater or equal to 1000: ${my_coins >= 1000}') // false

	/*
	I have 1000 coins.
	friend has 900 coins.
	friend's less than mine: true
	friend's not equal to mine: true
	I give friend 200 coins.
	friend's greater than mine: true
	friend gives me 150 coins.
	friend's equal to mine: true
	my coins is less than or equal to 900: false
	my coins is less than or equal to 950: true
	my coins is less than or equal to 1000: true
	my coins is greater or equal to 900: true
	my coins is greater or equal to 950: true
	my coins is greater or equal to 1000: false
	*/
}
```

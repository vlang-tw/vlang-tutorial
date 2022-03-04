# 變數

在V程式語言中，被宣告的變數預設是不可變的（immutable）。

```v
n := 5
```

不可變的變數在宣告後就不能再次賦值，必須使用`mut`關鍵字變數宣告為可變的（muttable）變數才能重新賦值。

```v
mut n := 10
n = 5
```

重新賦值要求新的值必須與變數原本持有的值具有相同的資料型別。

V程式語言要求宣告變數必須給定初始值，以避免空值導致應用程序崩潰。

變數宣告後不允許重新宣告同一個變數：

```v
x := 1
x := 2 // error: redefinition of x.
```

V程式語言有嚴格的變數命名規則：

* 變數名稱只能使用小寫字母，數字及底線命名
* 變數名稱只能使用小寫字母作開頭
* 採用底線劃分冗長的變數名稱 （**`snake_case`**）

V程式語言支援變數並行宣告及賦值：&#x20;

```v
// parallel immutable variable declaration
x, y, z := 4, 5, 6

// parallel mutable variable declaration
mut foo, mut bar := 'Hello', 'world'
foo, bar = 'Great', 'Nice'

// parallel declaration with mutable & immutable variable
mut r, pi = 2, 3.14
```

可變變數的擴增賦值語法：

```v
mut s := 'V '
s = s + 'programming '
s += 'tutorial' // augmented variable assignment

mut c := 0
c += 1
```

已宣告的變數至少被調用一次未被調用的變數都會導致編譯時在開發模式下產生警告，在生產模式下引發錯誤。

V程式語言預設不允許宣告全域變數，限制只能在函數內部中宣告變數。

```v
// main.v

module main

fn method() {
    s := 'Hello'
    println(s)
}

fn main() {
    method()
}
```

一些程式語言如Python有變數遮蔽（variable shadowing）的機制。

```python
def outer():
    x = 1 # outer variable
    
    def inner():
        x = 2 # inner variable
        print("inner", x)
    
    print("outer", x)
    inner()

outer()
# outer 1
# inner 2
```

當在內部作用域內(`def inner():`)宣告的變數與在外部作用域內(`def outer():`)宣告的變數具有相同的名稱（`x`）時，就會發生變數遮蔽，內部變數標識符掩蓋了外部變數標識符。

V程式語言不允許變數遮蔽，編譯時會引發錯誤。

```v
// main.v

module main

fn outer() {
    x := 1
    if true { // inner
        x := 10 // not allowed
        println(x)
    }
    println(x)
}

fn main() {
    outer()
}
```

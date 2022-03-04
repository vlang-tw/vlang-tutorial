# 常數

V程式語言使用`const關鍵字來宣告常數，必須在模組層級作用域中函式外部宣告常數。`

`常數的命名約定為`snake\_case`，僅能用小寫字母、數字及底線且必須以小寫字母作起始。`

```v
const app_version = '1.0.0'
```

當要宣告多個常數時，可使用括弧形成常數群組。

```v
const (
    app_version = '1.0.0'
    max_size = 1024
)
```

V程式語言允許用`struct`型別宣告常數：

```v
struct Point {
mut:
    x f32
    y f32
    z f32
}

const origin = Point {
    x: 0.0
    y: 0.0,
    z: 0.0
}
```

可以使用函式運算後的返回值來宣告常數：

```v
module main

struct Point {
mut:
	x f32
	y f32
	z f32
}

fn shift_y(p Point, offset f32) Point {
	return Point{
		x: p.x
		y: p.y + offset
		z: p.z
	}
}

const (
	origin = Point{
		x: 0.0
		y: 0.0
		z: 0.0
	}

	origin_y = shift_y(origin, 2.5)
)

fn main() {
	print(origin_y)
}
```

在函式內部宣告常數會導致編譯錯誤：

```v
module main

fn main() {
	const app_version = '1.0.0'
	// error: const can only be defined at the top level (outside of functions)
	print(app_version)
}
```

模組中引用常數必需添加模組名稱前綴來標識：

```v
module bar

const foo = 1

pub fn run() {
    print(bar.foo)
}
```

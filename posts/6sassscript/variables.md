## 基本用法

SASS中变量以`$`符标识，其他类似定义CSS属性。

```scss
$width: 100%;
#app {
    width: $width;
}

// 输出
#app {
  width: 100%;
}
```
## 作用域

变量的声明支持块级作用域，类同JavaScript的变量定义（函数作用域）。

```scss
#main {
    $width: 100%;
    width: $width
}

// 报错：ErrorError: Undefined variable.
// width: $width;
body {
  width: $width;
}
```

## global

块级作用域中支持用`!global`标识符声明全局变量，尽量不要使用这种形式。

```scss
#main {
    $width: 100% !global;
    width: $width;
}

// 输出，无报错
#main {
  width: 100%;
}

body {
  width: $width;
}
```

> 由于历史原因，变量名称（以及所有其他Sass标识符）可以互换使用连字符和下划线。例如，如果定义一个名为$ main-width的变量，则可以将其作为$ main_width访问，反之亦然。

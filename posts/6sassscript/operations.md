所有数据类型都支持判等运算，（`==`和`!=`），此外，每种类型都有一些自己的特殊操作类型。

## Number运算

SassScript 支持数字的加减乘除、取整等运算 (`+, -, *, /, %`)，如果必要会在不同单位间转换值。

```scss
#main {
    width: 100px + 1in + 2pt;
}

// 编译为CSS
#main {
  width: 198.6666666667px;
}
```

#### 除法运算

`/` 在 CSS 中通常起到分隔数字的用途，SassScript 作为 CSS 语言的拓展当然也支持这个功能，同时也赋予了 `/` 除法运算的功能。也就是说，如果 / 在 SassScript 中把两个数字分隔，编译后的 CSS 文件中也是同样的作用。

以下三种情况`/`将被视为除法运算符号：

1. 如果值或值的一部分，是变量或者函数的返回值；
2. 如果值被圆括号包裹；
3. 如果值是算数表达式的一部分

```scss
#main2 {
    font-size: 18px/12px;
    $width: 100px;
    width: $width/2; // use a variable
    width: round($number: 1)/2px; // function
    height: (500px/2); // parentheses
    margin-left: 5px + 8px/2; // expression
}

// 编译输出
#main2 {
  font-size: 18px/12px;
  width: 50px;
  width: 0.5;
  height: 250px;
  margin-left: 9px;
}

```

如果需要使用变量，同时又要确保 / 不做除法运算而是完整地编译到 CSS 文件中，只需要用 #{} 插值语句将变量包裹。

```scss
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
// 编译输出
p {
  font: 12px/30px; 
}
```

## Color运算

[Color运算](http://sass-lang.com/documentation/Sass/Script/Functions.html)

## String运算

`+` 连接字符串。

## 布尔运算

SassScript 支持布尔型的 and or 以及 not 运算。

## List运算

List不支持任何运算方式，只能使用 [list functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html#list-functions) 控制。

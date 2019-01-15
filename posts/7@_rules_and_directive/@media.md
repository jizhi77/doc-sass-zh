Sass 中 @media 指令与 CSS 中用法一样，只是增加了一点额外的功能：

1、 允许其在 CSS 规则中嵌套。如果 @media 嵌套在 CSS 规则内，编译时，@media 将被编译到文件的最外层，包含嵌套的父选择器。这个功能让 @media 用起来更方便，不需要重复使用选择器，也不会打乱 CSS 的书写流程。

```scss
.sidebar {
    width: 100px;
    @media screen and (max-width: 325px) {
        width: 200px;
    }
}
// 输出
.sidebar {
  width: 100px;
}
@media screen and (max-width: 325px) {
  .sidebar {
    width: 200px;
  }
}
```

2、 @media 的 queries 允许互相嵌套使用，编译时，Sass 自动添加 `and`

```scss
@media screen and (min-width: 325px) {
    .sidebar {
        width: 100px;
        @media screen and (max-width: 340px) {
            width: 200px;
        }
    }
}
// 输出
@media screen and (min-width: 325px) {
  .sidebar {
    width: 100px;
  }
}
@media screen and (min-width: 325px) and (max-width: 340px) {
  .sidebar {
    width: 200px;
  }
}
```

3、 @media 甚至可以使用 SassScript（比如变量，函数，以及运算符）代替条件的名称或者值：

```scss
$media: screen;
$feature: device-pixel-ration;
$feature_value: 1.5;
@media #{$media} and ($feature: $feature_value) {
    #sidebar {
        width: 100px;
    }
}
// 输出
@media screen and (-webkit-min-device-pixel-ratio: 1.5) {
  #sidebar {
    width: 100px;
  }
}
```

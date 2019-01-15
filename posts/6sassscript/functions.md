SassScript 定义了多种函数，有些甚至可以通过普通的 CSS 语句调用。

有两种调用方式：

```scss
div {
    color: hsl(0, 100%, 50%);
    background: hsl($hue: 0, $saturation: 100%, $lightness: 50%)
}
```

可以通过 [Sass::Script::Functions](http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html) 查看完整的 Sass 函数列表，参数名，以及如何自定义函数。

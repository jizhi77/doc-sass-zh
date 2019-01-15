语法形式： `#{}`。

- 选择器名（拼接）；
- 属性名（拼接）；
- 属性值（避免 Sass 运行运算表达式，直接编译输出 CSS）；

```scss
$name: foo;
$attr: border;
p .#{$name} {
    #{$attr}-left: 1px solid #e1e1e1;
}

// 编译输出CSS

p .foo {
  border-left: 1px solid #e1e1e1;
}
```

有些 CSS 属性遵循相同的命名空间 (namespace)，比如 font-family, font-size, font-weight 都以 font 作为属性的命名空间。为了便于管理这样的属性，同时也为了避免了重复输入，Sass 允许将属性嵌套在命名空间中，例如：

```scss
.fuck {
    font: 20px {
        family: fantasy;
        weight: 400;
    }
    padding: {
        top: 10px;
        left: 10px;
    }
}
```

编译为：

```css
.fuck {
  font: 20px;
  font-family: fantasy;
  font-weight: 400;
  padding-top: 10px;
  padding-left: 10px;
}
```

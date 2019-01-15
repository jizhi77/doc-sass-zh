Sass 允许将一套 CSS 样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器

```scss
// SCSS
#app {
    .head,
    .content p {
        width: 100%;
    }
    div {
        color: red;
    }
}
//输出CSS
#app .head,
#app .content p {
  width: 100%;
}
#app div {
  color: red;
}
```

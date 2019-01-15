## 伪类、伪元素

```scss
// SCSS-伪类
#app {
    a {
        text-decoration: none;
        color: black;
    }
    &:hover {
        color: red;
    }
}

// SCSS-伪元素
#app {
    p {
        width: 100%;
    }
    &:nth-child(2n+1) {
        background: #e1e1e1;
    }
}

// 输出CSS
#app a {
  text-decoration: none;
  color: black;
}
#app:hover {
  color: red;
}

#app p {
  width: 100%;
}
#app:nth-child(2n+1) {
  background: #e1e1e1;
}
```

## 选择器名称拼接

```scss
#app {
    .head {
        width: 100%;
    }
    &-conent {
        color: red;
    }
}

// 输出CSS
#app .head {
  width: 100%;
}
#app-conent {
  color: red;
}
```

> 注意，一般使用父级选择器引用，嵌套规则失效

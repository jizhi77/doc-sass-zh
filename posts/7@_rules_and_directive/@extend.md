## 基础使用

`@extend`继承某个已有样式的所有属性设置。

```scss
.comon-error {
    border: 1px solid #ff00ff;
    background-color: #ffddff;
}

.serious-error {
    @extend .comon-error;
    border-width: 3px;
}
// 输出
.comon-error, .serious-error {
  border: 1px solid #ff00ff;
  background-color: #ffddff;
}

.serious-error {
  border-width: 3px;
}
```

## 多重延伸

```scss
.error {
    border: 1px solid #ff00ff;
    background-color: #ff00ff;
}

.attention {
    border: 1px solid red;
    color: red;
}

.serious {
    @extend .error;
    @extend .attention;
    padding: {
        top: 20px;
        left: 20px;
    }
}
// 输出
.error, .serious {
  border: 1px solid #ff00ff;
  background-color: #ff00ff;
}

.attention, .serious {
  border: 1px solid red;
  color: red;
}

.serious {
  padding-top: 20px;
  padding-left: 20px;
}
```

可以extend多个选择器属性，优先级按照先后顺序为准。

## 链式延伸

```scss
.error {
    border: 1px solid #ff00ff;
    background-color: #ff00ff;
}

.attention {
    @extend .error;
    color: red;
}

.serious {
    @extend .attention;
    padding: {
        top: 20px;
        left: 20px;
    }
}
// 输出
.error, .attention, .serious {
  border: 1px solid #ff00ff;
  background-color: #ff00ff;
}

.attention, .serious {
  color: red;
}

.serious {
  padding-top: 20px;
  padding-left: 20px;
}
```

## extend-only

有时，需要定义一套样式并不是给某个元素用，而是只通过 @extend 指令使用，尤其是在制作 Sass 样式库的时候，希望 Sass 能够忽略用不到的样式。

```scss
%placeholder {
    color: black;
    font: 12px/18px {
        family: Seria;
        weight: 500;
    }
}

.paragraph {
    @extend %placeholder;
    color: #ff00ff;
    background: red;
}

.title {
    @extend %placeholder;
    text-align: center;
}
// 输出
.title, .paragraph {
  color: black;
  font: 12px/18px;
  font-family: Seria;
  font-weight: 500;
}

.paragraph {
  color: #ff00ff;
  background: red;
}

.title {
  text-align: center;
}
```


> 延伸后的结果其实就是提取共同属性定义到某一个选择器分组中。



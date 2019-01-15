混合指令（Mixin）用于定义可重复使用的样式，避免了使用无语意的 class，比如 .float-left。混合指令可以包含所有的 CSS 规则，绝大部分 Sass 规则，甚至通过参数功能引入变量，输出多样化的样式。

## 定义及使用

#### 定义

Mixins功能使用`@mixin`指令定义，后面紧跟mixin的名称和可选的参数，最后是包含mixin内容的块。例如，一个`large-text`的mixin定义如下：

```scss
@mixin large-text() {
    font: 12px/14px {
        family: Arial;
        size: 20px;
        weight: bold;
    }
    color: #ff0000;
}
```

#### 使用

使用 @include 指令引用混合样式，格式是在其后添加混合名称，以及需要的参数（可选）：

```scss
.page-title {
  @include large-text;
  padding: 4px;
  margin-top: 10px;
}
```

#### 特例1

Sass也支持在最外层引用混合样式，此时不可以直接定义属性，也不可以使用父选择器。

```scss
@mixin silly-links {
  a {
    color: blue;
    background-color: red;
  }
}
@include silly-links;
// 编译为
a {
  color: blue;
  background-color: red; 
}
```

#### 特例2

Sass还支持在mixin中引入其他mixin，例如：

```scss
@mixin highlighted-background { background-color: #fc0; }
@mixin header-text { font-size: 20px; }
@mixin compound {
  @include highlighted-background;
  @include header-text;
}

.compand {
  @include compand();
}
```

## 参数

参数用于给混合指令中的样式设定变量，并且赋值使用。在定义混合指令的时候，按照变量的格式，通过逗号分隔，将参数写进圆括号里。引用指令时，按照参数的顺序，再将所赋的值对应写进括号：

```scss
@mixin sexy-border($color, $width) {
    border: {
        color: $color;
        width: $width;
        style: solid;
    }
}
p {@include sexy-border(red,5px)} 
```

#### 默认参数

混合指令也可以使用给变量赋值的方法给参数设定默认值，然后，当这个指令被引用的时候，如果没有给参数赋值，则自动使用默认值：


```scss
@mixin sexy-border($color, $width: 10px) {
    border: {
        color: $color;
        width: $width;
        style: solid;
    }
}
p {@include sexy-border(red)} 
```

#### 关键词参数

混合指令也可以使用关键词参数：

```scss
p{@include sexy-border($width: 10px,$color: red)}
```

> 关键词参数指调用mixin时，指定参数名，因此顺序不再是强制的。



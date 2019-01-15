`@each`类似于编程语言中的`for in`。

## 语法

```scss
@each $var in list {
     
}
```

## 单列表

```scss
@each $animal in puma, sea-slug, egret, salamander {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}
// 编译为
.puma-icon {
  background-image: url("/images/puma.png");
}

.sea-slug-icon {
  background-image: url("/images/sea-slug.png");
}

.egret-icon {
  background-image: url("/images/egret.png");
}

.salamander-icon {
  background-image: url("/images/salamander.png");
}
```

## 多列表

```scss
@each $animal, $color, $cursor in (puma, black, default),
                                  (sea-slug, blue, pointer),
                                  (egret, white, move) {
  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
    border: 2px solid $color;
    cursor: $cursor;
  }
}
// 编译为
.puma-icon {
  background: url("/images/animal.png");
  border: 2px solid black;
  cursor: default;
}

.sea-slug-icon {
  background: url("/images/animal.png");
  border: 2px solid blue;
  cursor: point;
}

.egret-icon {
  background: url("/images/animal.png");
  border: 2px solid white;
  cursor: move;
}
```



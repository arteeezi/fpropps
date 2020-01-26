Жидкие свойства scss
========================

```scss
@mixin fprop($property, $min, $max, $minVw: 375, $maxVw: 1920)  {
  $tmp: $max - $min;
  $tmpVw: $maxVw - $minVw;

  #{$property}: #{$min}px;

  @media screen and (min-width: #{$maxVw}px){
    #{$property}: #{$max}px;
  }

  @media screen and (min-width: #{$minVw}px) {
    #{$property}: calc(#{$min}px + #{$tmp} * ((100vw - #{$minVw}px) / #{$tmpVw}));
  }
}
```

Использование
```
.test-h1 {
  @include fprop(*свойство*, *min значение*, *max значение*, *min ширина экрана*, *max ширина экрана*);
}

.test-h1 {
  @include fprop("font-size", 12, 55, 375, 800);
}
```

[Результат](http://g.recordit.co/WMwMkdqkTD.gif)

[Сборка](https://github.com/artem-Zrilov/frontend-pack)

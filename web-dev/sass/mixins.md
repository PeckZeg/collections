SASS/SCSS Mixins
================

## `@include size(width[, height])`

```scss
@mixin size($size...) {
  $size: if(length($size) > 0, $size, auto);
  $width: nth($size, 1);
  $height: nth($size, length($size));

  @if $width != auto {
    $width: if(unitless($width), $width + px, $width);
  }
  @if $height != auto {
    $height: if(unitless($height), $height + px, $height);
  }

  width: $width;
  height: $height;
}
```

## `@include rem($properties, $values)`

[sass-rem](https://github.com/pierreburel/sass-rem)

条件注释
========

## `<html>` 加上 ie 7 ~ 9 的前缀

```html
<!--[if IE 9]><html class="ie9"><![endif]-->
<!--[if IE 8]><html class="ie8"><![endif]-->
<!--[if IE 7]><html class="ie7"><![endif]-->
<!--><html><!--<![endif]-->
```

## IE 9 或其他非 IE 浏览器

```html
<!--[if (gte IE 9) | (!IE) ]><!-->
    <script type="text/javascript" src="/jquery-2.1.1.min.js"></script>
<!--<![endif]-->
```

## IE 8 及以下的老式浏览器

```html
<!--[if lte IE 8]>
    <script type="text/javascript" src="/acgdb-cms-v2.lib.oldie.min.js"></script>
<![endif]-->
```
使用 Grunt 构建 SASS/SCSS
=========================

> 添加时间: `2015-12-21`

最近开始使用基于 [Sass/Scss][sass-lang] 的 [Compass][compass] 进行 CSS 的预编译，这必不可免的要将其塞到 [Grunt][grunt] 中进行整个项目的构建。在折腾了这一串的东西之后，觉得有必要写点什么，以防以后脑抽的时候能够有一个能够比较适合自己的教程。

## 工具

* [`Sass/Scss`][sass-lang]
* [`Compass`][compass]
* [`Grunt`][grunt]
    - [`grunt-compass`][grunt-compass]
    - [`grunt-contrib-rename`][grunt-contrib-rename]
    - [`grunt-autoprefixer`][grunt-autoprefixer]
    - [`grunt-contrib-cssmin`][grunt-contrib-cssmin]

## 流程

我个人想通过编译总控制文件 `!.scss` 成一个 `project.css` 文件，然后通过 `cssmin` 再将其压缩成一个 `project.min.css` 的版本。

### 工程目录结构

```
|- src/
  |- scss/
    |- elements/
    |- frames/
    |- mixins/
    |- variables/
    |- !.scss
    |- base.scss
    |- mixins.scss
    |- variables.scss
|- dest/
  |- css/
    |- project.css
    |- project.min.css
```

### 1. 将 Sass/Scss 编译为 CSS 文件

[`grunt-compass`][grunt-compass]、[`grunt-contrib-rename`][grunt-contrib-rename] 这套组合将使得 Sass/Scss 文件能够按照我们的意思编译、改名为指定的文件。

编写的配置文件将如下所示（我们将为该项目统一建立一个名为 `project` 的子任务）：

```
{
    compass: {

        //  指定子任务
        project: {
            options: {
                linecomments: false,            //  不输出注释
                sassDir: 'src/scss',            //  Sass/Scss 的文件目录
                specify: 'src/scss/!.scss',     //  指定文件
                cssDir: 'dest/css',             //  输出 Css 的文件目录
            }
        }
    },

    rename: {

        //  指定子任务
        project: {
            files: [{
                src: ['dest/css/!.css'],        //  源文件
                dest: 'dest/css/project.css'    //  输出文件（会将源文件移除）
            }]
        }
    },
}
```

### 2. 为输出的文件补齐浏览器前缀（最大兼容性）

使用 [`grunt-autoprefixer`][grunt-autoprefixer] 工具能为 Css 文件补齐浏览器前缀（比如 `-webkit-`），编写的 Grunt 配置如下

```
{
    autoprefixer: {
        project: {
            options: {
                browsers: ['last 2 versions', 'ie 7', 'ie 8', 'ie 9'],
                map: true
            },
            src: 'dest/css/project.css',
            dest: 'dest/css/project.css'
        }
    }
}
```

### 3. 压缩 Css 文件，最终生成 `project.min.css`

使用 [`grunt-contrib-cssmin`][grunt-contrib-cssmin] 将 Css 文件压缩到最小尺寸，编写的 Grunt 配置如下

```
{
    cssmin: {
        project: {
            options: {
                shorthandCompacting: false,
                roundingPrecision: -1
            },

            files: [{
                src: '<%= rename.scss.files[0].dest %>',
                dest: 'dest/css/wado-promotion.tbc.min.css',
            }],
        }
    }
}
```



[sass-lang]: http://sass-lang.com/
[compass]: http://compass-style.org/
[grunt]: http://gruntjs.com/
[autoprefixer]: https://github.com/postcss/autoprefixer
[grunt-compass]: https://www.npmjs.com/package/grunt-compass
[grunt-contrib-rename]: https://www.npmjs.com/package/grunt-contrib-rename
[grunt-autoprefixer]: https://www.npmjs.com/package/grunt-autoprefixer
[grunt-contrib-cssmin]: https://www.npmjs.com/package/grunt-contrib-cssmin
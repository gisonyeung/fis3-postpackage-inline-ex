
# fis3-postpackager-inline-ex

将HTML引用的资源文件内联，支持配置内联大小以及排除项。

本插件修改自 [imweb/fis3-postpackager-inline](https://github.com/imweb/fis3-postpackager-inline)，在原有插件基础上增加了一个功能。


## Install

```sh
npm install fis3-postpackager-inline
```

## Usage

```js
fis.media('dist')
    .match('::packager', {
        postpackager: [
            fis.plugin('inline')
        ]
    })
```

## Options

### max `{Number}`

`default` 25

inline文件总最大kb数

### jsMax `{Number}`

`default` 10

inline js文件最大kb数

### cssMax `{Number}` 

`default` 20

inline css文件最大kb数

### excludes `{String | Array}`
`default` []

资源URL中含有关键字的文件不进行内联。

该功能简单使用`.indexOf()`方法实现，可以指定不内联具体路径的所有文件，也可以指定不内联某个具体文件。

如果采用了`useHash`功能，则应该不传入后缀。例如希望排除`lib.bundle.js`文件，则`excludes`应该传入`['lib.bundle']`而不是`['lib.bundle.js']`，因为文件被hash之后的名称为`lib.bundle_{hash}.js`。
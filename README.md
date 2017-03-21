# package.json

**npm package.json**  配置介绍

## `name` 包名

`package-guide-notes`

**必须**

`name`和`version`一起组成的标识在假设中是唯一的。改变包应该同时改变version

- 长度小于214个字符
- 不能以`.` `_`开头
- 不能包含大写字母
- 名字会作为在URL的一部分、命令行的参数或者文件夹的名字。任何non-url-safe的字符都是不能用的
- 不要把node或者js放在名字中。因为你写了package.json它就被假定成为了js，不过你可以用"engine"字段指定一个引擎

## `version` 版本

`1.0.0`

**必须**

## description 描述

包描述信息，便于搜索或阐述包作用

## `keywords` 关键字

`package` `npm`

包关键字，字符串数组，便于搜索

## homepage 项目官网地址

`https://github.com/Gnotes/package.json`

## bugs 提问的地方

- `url` 指向项目`issue`地址

`https://github.com/Gnotes/package.json/issues`

- `email` 指向发送bug的邮箱

`example@github.com`

## license 协议

- 单个协议

```
{ "license" : "ISC" }

{ "license" : "MIT" }
```

```
{ "license" : "BSD-3-Clause" }
```

- 多个协议

```
{ "license" : "(ISC OR GPL-3.0)" }
```

- 指定协议文件

top level of the package,与package.json文件相同目录下

```
{ "license" : "SEE LICENSE IN <filename>" }
```

- 不指定协议

```
{ "license": "UNLICENSED"}
```

## author 作者 & contributors 协助者

- 作者是一个人（person）：{name : "xing.he", email : "example@github.com", url : "https://xxx" }对象， 协助者是个person对象数组    
  person是一个有name字段，可选的有url、email字段的对象
- author也可以是字符串`"xing.he <example@github.com> (https://xxx)"`
- email也可以是字符数组

```
{
  "name": "xing.he",
  "email": [
    "abc@gmail.com",
    "xing@github.com"
  ]
}
```

## files 包含文件（夹）

files是一个包含项目中的文件的数组。如果命名了一个文件夹，那也会包含文件夹中的文件，你也可以提供一个.npmignore文件，让即使被包含在files字段中得文件被忽略

### 不被忽略的文件

- package.json 
- README (and its variants) 
- CHANGELOG (and its variants) 
- LICENSE / LICENCE 

### 一定被忽略的文件

- .git
- CVS
- .svn
- .hg
- .lock-wscript
- .wafpickle-N
- *.swp
- .DS_Store
- ._*
- npm-debug.log

## main 文件入口

## bin 可执行文件目录

很多包都有一个或多个可执行的文件希望被放到PATH中，要用这个功能，给package.json中的bin字段一个命令名到文件位置的map。初始化的时候npm会将他链接到prefix/bin（全局初始化）或者./node_modules/.bin/（本地初始化）    

比如，npm有：
```
{ "bin" : { "npm" : "./cli.js" } }
```

## man

## directories

### directories.lib

### directories.bin

### directories.man

### directories.doc

### directories.example

## repository 仓库地址

```
"repository" :{ 
  "type" : "git", 
  "url" : "http://github.com/isaacs/npm.git"
}

"repository" :{
   "type" : "svn", 
   "url" : "http://v8.googlecode.com/svn/trunk/"
}
```

## scripts 执行脚本命令项

一个{"key" : "value"}对象,key为命令参数，value是要执行的真实命令   

```
"scripts": {                                            
  "test": "echo \"Error: no test specified\" && exit 1",
  "start": "node ./bin/start"       
}
```

## dependencies 项目必须的依赖

- `version` 必须完全和`version`一致
- `>version` 必须比version大
- `>=version` 大于等于
- `<version` 小于
- `<=version` 小于
- `~version` 约等于
- `1.2.x` `1.2.0` `1.2.1`等，但不包括`1.3.0`
- `http://...` 见下文'依赖URL'
- `*` 所有
- `""` 空，同*
- `range1 || range2` 二选一
- `git...` 见下文'依赖Git URL'
- `user/repo` 见下文'GitHub URLs'

```
"dependencies" :{ 
  "foo" : "1.0.0 - 2.9999.9999",
  "bar" : ">=1.0.2 <2.1.2",
  "baz" : ">1.0.2 <=2.3.4",
  "boo" : "2.0.1",
  "qux" : "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0",
  "asd" : "http://asdf.com/asdf.tar.gz",
  "til" : "~1.2",
  "elf" : "~1.2.3",
  "two" : "2.x",
  "thr" : "3.3.x"
}
```

### Git urls 可以是下面几种形式：

```
git://github.com/user/project.git#commit-ish
git+ssh://user@hostname:project.git#commit-ish
git+ssh://user@hostname/project.git#commit-ish
git+http://user@hostname/project/blah.git#commit-ish
git+https://user@hostname/project/blah.git#commit-ish
```

## devDependencies 开发模式依赖包

## engines 指定node引擎版本

```
{ "engines" : { "node" : ">=0.10.3 <0.12" } }
```

或者

```
{ "engines" : { "npm" : "~1.0.20" } }
```


## 参考文献

- [package.json](https://docs.npmjs.com/files/package.json)   
- [package.json](http://mujiang.info/translation/npmjs/files/package.json.html)   
- [what the difference between ~ and ^ in package.json](http://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json)   

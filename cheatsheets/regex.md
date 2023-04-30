# 正则表达式速查表

> [原教程链接](https://regexlearn.com/zh-cn/learn)，推荐使用 `Ctrl+F` 进行查找🔎

正则表达式，即 Regular Expressions，缩写为 Regex 或 Regexp，是在正则表达式语法框架内创建的字符串。您可以用正则表达式轻松管理数据，执行查找、匹配或编辑等命令。正则表达式适用于 Python、SQL、JavaScript、R、Google Analytics、Google Data Studio 等编程语言和整个编程过程。


## 锚点

:::details `^` 行或字符串的开头
匹配字符串或行的开头，如 `/^\w+/`

==an== answer or a question
:::

:::details `$` 行或字符串的末尾
匹配字符串或行的末尾，如 `/\w+$/`

an answer or a ==question==
:::

:::details `\b` 单词边界
匹配单词的开头或末尾，如 `/n\b/`

a==n== answer or a questio==n==
:::

:::details `\B` 非单词边界
匹配不在单词开头或末尾的位置，如 `/n\B/`

an a==n==swer or a question
:::


## 量词与分支

:::details `+` 加号
表达式匹配一个或多个，如 `/be+p/g`

bp ==bep== ==beep== ==beeep==
:::

:::details `*` 星号
表达式匹配零个或多个，如 `/be*p/g`

==bp== ==bep== ==beep== ==beeep==
:::

:::details `{1, 3}` 重复
表达式匹配指定范围的位数，如 `/be{1,2}p/g`

bp ==bep== ==beep== beeep
:::

:::details `?` 可选
表达式匹配指定范围的位数，如 `/colou?r/g`

==color== ==colour==
:::

:::details `|` 分支
类似于“或”，用于匹配多种符合条件的表达式之一，如 `/(c|r)at/g`

fat ==cat== ==rat==
:::


## 字符类

:::details `[abc]` 字符集
匹配集合中的任意字符，如 `/b[eo]r/`

bar ==ber== bir ==bor== bur
:::

:::details `[^abc]` 否定字符集
匹配不在集合中的任意字符，如 `/b[^eo]r/`

==bar== ber ==bir== bor ==bur==
:::

:::details `[a-z]` 范围
匹配两个字符之间的任意字符，包括它们本身，如 `/[e-i]/`

abcd==efghi==jklmnopqrstuvwxyz
:::

:::details `.` 点
匹配除换行符之外的任意字符，如 `/./`

==hi012_-!?==
:::

:::details `\w` 单词
匹配字母、数字或下划线，如 `/\w/`

==hi012_==-!?
:::

:::details `\W` 非单词
匹配除字母、数字和下划线之外的任意字符，如 `/\W/`

hi012_==-!?==
:::

:::details `\d` 数字
匹配所有数字，如 `/\d/`

+==1==-(==444==)-==222==
:::

:::details `\D` 非数字
匹配除数字外的任意字符，如 `/\D/`

<mark>+</mark>1<mark>-(</mark>444<mark>)-</mark>222
:::

:::details `\s` 空白符
匹配所有空白字符，如 `/\s/`，因无法对空白字符划线故省略示例
:::

:::details `\S` 非空白符
匹配除空白字符以外的任意字符，如 `/\S/`

==one== ==two==
:::

## 标志

:::details `i` 忽略大小写
使表达式忽略大小写，如 `/cat/i`

==CaT==
:::

:::details `g` 全局
确保表达式不会在检索到第一个匹配项时停止，如 `/cat/g`

==cat== ==cat== ==cat==
:::

:::details `m` 多行
如果不启用，`^` 和 `$` 只匹配整个字符串的开始和结束，而不会单独匹配每一行，如 `/cat/m`

==cat== 

==cat== 
:::


## 组和引用

:::details `()` 组
使表达式分组，如 `/(ha)+/g`

==hahaha== ==ha==h ==haha==
:::

:::details `\1` 引用
引用表达式的分组，如 `/(\w)a\1/g`

==hah== haa ==dad==
:::

:::details `(?:)` 非捕获组
创建无法引用的分组，如 `/(?:ha)+/g`

==hahaha== ==ha==h ==haha==
:::


## 零宽断言

:::details `(?=)` 正向先行断言
如 `/\d(?=nd)/g`

1st ==2==nd 3pc
:::


:::details `(?!)` 负向先行断言
如 `/\d(?!nd)/g`

==1==st 2nd ==3==pc
:::

:::details `(?<=)` 正向后行断言
如 `/(?<=%)\d/g`

#1 $2 %==3==
:::

:::details `(?<!)` 负向后行断言
如 `/(?<!%)\d/g`

#==1== $==2== %3
:::
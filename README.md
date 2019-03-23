<p align="center"><img src="https://raw.githubusercontent.com/odb/official-bash-logo/master/assets/Logos/Icons/PNG/512x512.png" width="200px"></p>
<h1 align="center">pure bash bible</h1> <p
align="center">A collection of pure bash alternatives to external
processes.</p>

<p align="center"> <a
href="https://travis-ci.com/dylanaraps/pure-bash-bible"><img
src="https://travis-ci.com/dylanaraps/pure-bash-bible.svg?branch=master"></a>
<a href="https://discord.gg/yfa5BDw"><img src="https://img.shields.io/discord/440354555197128704.svg"></a>
<a href="./LICENSE.md"><img
src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
</p>

<br>

<a href="https://leanpub.com/bash/">
<img src="https://s3.amazonaws.com/titlepages.leanpub.com/bash/hero" width="40%" align="right">
</a>

The goal of this book is to document commonly-known and lesser-known methods of doing various tasks using only built-in `bash` features. Using the snippets from this bible can help remove unneeded dependencies from scripts and in most cases make them faster. I came across these tips and discovered a few while developing [neofetch](https://github.com/dylanaraps/neofetch), [pxltrm](https://github.com/dylanaraps/pxltrm) and other smaller projects.

The snippets below are linted using `shellcheck` and tests have been written where applicable. Want to contribute? Read the [CONTRIBUTING.md](https://github.com/dylanaraps/pure-bash-bible/blob/master/CONTRIBUTING.md). It outlines how the unit tests work and what is required when adding snippets to the bible.

See something incorrectly described, buggy or outright wrong? Open an issue or send a pull request. If the bible is missing something, open an issue and a solution will be found.

<br>
<p align="center"><b>This book is also available to purchase on leanpub. https://leanpub.com/bash</b></p>
<p align="center"><b>Or you can buy me a coffee.</b>
<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=V7QNJNKS3WYVS"><img src="https://img.shields.io/badge/don-paypal-yellow.svg"></a> <a href="https://www.patreon.com/dyla"><img src="https://img.shields.io/badge/don-patreon-yellow.svg"> </a><a href="https://liberapay.com/2211/"><img src="https://img.shields.io/badge/don-liberapay-yellow.svg"></a>
</p>

<br>

# Table of Contents

<!-- vim-markdown-toc GFM -->

* [序言](#序言)
* [字符串](#字符串)
    * [`Trim` 去掉`两边`空格](#Trim-去掉两边空格)
    * [`Trim` 去掉`两边`空格，并`压缩` `中间`的空格为一个空格](#Trim-去掉两边空格并压缩中间的空格为一个空格)
    * [字符串使用`正则`获取`分组`](#字符串使用正则获取分组)
    * [`Split` 分割字符串](#Split-分割字符串)
    * [转小写](#转小写)
    * [转大写](#转大写)
    * [`去掉`字符串里面的`引号`](#去掉字符串里面的引号)
    * [从字符串中`删掉`所有`匹配`到的内容](#从字符串中删掉所有匹配到的内容)
    * [从字符串中`删掉` `第一个匹配`到的内容](#从字符串中删掉第一个匹配到的内容)
    * [从字符串`开头` `删除`匹配到的内容](#从字符串开头删除匹配到的内容)
    * [从字符串的`结尾` `删除`匹配到的内容](#从字符串的结尾删除匹配到的内容)
    * [url编码](#url编码)
    * [url解码](#url解码)
    * [是否`包含`某子串](#是否包含某子串)
    * [是否以某`子串开头`](#是否以某子串开头)
    * [是否以某`子串结尾`](#是否以某子串结尾)
* [数组](#数组)
    * [`Reverse` 一个数组](#Reverse-一个数组)
    * [`去重`，得到set](#去重得到set)
    * [从数组`随机取`一个元素](#从数组随机取一个元素)
    * [`打圈`地循环数组](#打圈地循环数组)
    * [`Toggle` 切换两个值](#Toggle-切换两个值)
* [循环](#循环)
    * [遍历数字范围](#遍历数字范围)
    * [普通循环0-i](#普通循环0-i)
    * [遍历数组元素](#遍历数组元素)
    * [以index来遍历数组](#以index来遍历数组)
    * [一行一行地遍历文件内容](#一行一行地遍历文件内容)
    * [遍历文件和目录](#遍历文件和目录)
* [文件处理](#文件处理)
    * [`读取`文件内容`到一个字符串`](#读取文件内容为一个字符串)
    * [`读取`文件内容`到数组`一行一个元素](#读取文件内容到数组一行一个元素)
    * [获取文件`前N行`](#获取文件前N行)
    * [获取文件`后N行`](#获取文件后N行)
    * [获取文件`行数`](#获取文件行数)
    * [获取目录下有多少个东西（文件或目录）](#获取目录下有多少个东西文件或目录)
    * [创建`空文件`](#创建空文件)
    * [`提取`两行标记之间的`内容`](#提取两行标记之间的内容)
* [文件路径](#文件路径)
    * [获取所在目录](#获取所在目录)
    * [获取base-name，即去掉路径的目录部分](#获取base-name即去掉路径的目录部分)
* [变量](#变量)
    * [嵌套变量，动态变量](#嵌套变量动态变量)
    * [动态变量名，即基于变量来定义另外一个变量](#动态变量名即基于变量来定义另外一个变量)
* [转义字符串](#转义字符串)
    * [文本`颜色`](#文本颜色)
    * [文本属性](#文本属性)
    * [`光标移动`](#光标移动)
    * [`删除文本`](#删除文本)
* [变量扩展](#变量扩展)
    * [Indirection](#indirection)
    * [替换](#替换)
    * [长度](#长度)
    * [扩展](#扩展)
    * [大小写转换](#大小写转换)
    * [默认值](#默认值)
* [花括号扩展](#花括号扩展)
    * [范围{a..b}](#范围ab)
    * [列表{a,b}](#列表ab)
* [条件表达式test](#条件表达式test)
    * [`文件条件语句`](#文件条件语句)
    * [文件比较](#文件比较)
    * [`变量条件语句`](#变量条件语句)
    * [变量比较](#变量比较)
* [算术操作](#算术操作)
    * [赋值](#赋值)
    * [算数](#算数)
    * [位运算](#位运算)
    * [逻辑](#逻辑)
    * [杂项](#杂项)
* [计算](#计算)
    * [简单计算](#简单计算)
    * [三目表达式](#三目表达式)
* [捕获信息](#捕获信息)
    * [脚本`结束`时`干些事情`](#脚本结束时干些事情)
    * [忽略终端打断(CTRL+C, SIGINT)](#忽略终端打断-ctrlc-sigint)
    * [React to window resize](#react-to-window-resize)
    * [每个命令`之前` `干些事情`](#每个命令之前干些事情)
    * [方法`执行后` `干些事情`](#方法执行后干些事情)
* [PERFORMANCE](#performance)
    * [关闭 Unicode](#关闭-unicode)
* [旧语法](#旧语法)
    * [Shebang](#shebang)
    * [命令替换](#命令替换)
    * [方法的定义](#方法的定义)
* [内置变量](#内置变量)
    * [bash二进制路径](#bash二进制路径)
    * [bash版本](#bash版本)
    * [用户首选到编辑器](#用户首选到编辑器)
    * [获取方法的名字](#获取方法的名字)
    * [获取主机名`hostname`](#获取主机名hostname)
    * [获取`系统架构`](#获取系统架构)
    * [获取`系统名称`](#获取系统名称)
    * [取当前工作目录`pwd`](#取当前工作目录pwd)
    * [获取脚本运行了多长时间](#获取脚本运行了多长时间)
    * [获取`随机整数`0-32767](#获取随机整数0-32767)
* [终端信息](#终端信息)
    * [在脚本里获取`窗口大小`，几行几列](#在脚本里获取窗口大小几行几列)
    * [获取`终端像素`](#获取终端像素)
    * [获取`光标位置`](#获取光标位置)
* [转换](#转换)
    * [哈希颜色 转 RGB](#哈希颜色-转-rgb)
    * [RGB 转 哈希颜色](#rgb-转-哈希颜色)
* [更简单的代码写法](#更简单的代码写法)
    * [更短的`for`语法](#更短的for语法)
    * [更短的无限循环](#更短的无限循环)
    * [更短的方法定义](#更短的方法定义)
    * [更短的`if`语法](#更短的if语法)
    * [更简单的`switch`设置变量](#更简单的switch设置变量)
* [其他](#other)
    * [用`read`代替`sleep`命令](#用read代替sleep命令)
    * [程序是否在环境变量PATH的目录里, `程序是否安装`](#程序是否在环境变量PATH的目录里程序是否安装)
    * [利用printf获取`当前时间`](#利用printf获取当前时间)
    * [获取当前用户的用户名](#获取当前用户的用户名)
    * [生成 `UUID` V4](#生成-uuid-v4)
    * [进度条](#进度条)
    * [获取脚本的所有方法列表](#获取脚本的所有方法列表)
    * [Bypass shell aliases](#bypass-shell-aliases)
    * [Bypass shell functions](#bypass-shell-functions)
    * [后台运行](#后台运行)
* [AFTERWORD](#afterword)

<!-- vim-markdown-toc -->

<br>

<!-- CHAPTER START -->
# 序言

A collection of pure `bash` alternatives to external processes and programs. The `bash` scripting language is more powerful than people realise and most tasks can be accomplished without depending on external programs.

Calling an external process in `bash` is expensive and excessive use will cause a noticeable slowdown. Scripts and programs written using built-in methods (*where applicable*) will be faster, require fewer dependencies and afford a better understanding of the language itself.

The contents of this book provide a reference for solving problems encountered when writing programs and scripts in `bash`. Examples are in function formats showcasing how to incorporate these solutions into code.

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 字符串

## Trim 去掉两边空格

This is an alternative to `sed`, `awk`, `perl` and other tools. The
function below works by finding all leading and trailing white-space and
removing it from the start and end of the string. The `:` built-in is used in place of a temporary variable.

**Example Function:**

```sh
trim_string() {
    # Usage: trim_string "   example   string    "
    : "${1#"${1%%[![:space:]]*}"}"
    : "${_%"${_##*[![:space:]]}"}"
    printf '%s\n' "$_"
}
```

**Example Usage:**

```shell
$ trim_string "    Hello,  World    "
Hello,  World

$ name="   John Black  "
$ trim_string "$name"
John Black
```

## Trim 去掉两边空格，并压缩中间的空格为一个空格

This is an alternative to `sed`, `awk`, `perl` and other tools. The
function below works by abusing word splitting to create a new string
without leading/trailing white-space and with truncated spaces.

**Example Function:**

```sh
# shellcheck disable=SC2086,SC2048
trim_all() {
    # Usage: trim_all "   example   string    "
    set -f
    set -- $*
    printf '%s\n' "$*"
    set +f
}
```

**Example Usage:**

```shell
$ trim_all "    Hello,    World    "
Hello, World

$ name="   John   Black  is     my    name.    "
$ trim_all "$name"
John Black is my name.
```

## 字符串使用正则获取分组

The result of `bash`'s regex matching can be used to replace `sed` for a
large number of use-cases.

**CAVEAT**: This is one of the few platform dependent `bash` features.
`bash` will use whatever regex engine is installed on the user's system.
Stick to POSIX regex features if aiming for compatibility.

**CAVEAT**: 这个例子只是获取第一个分组，如果你需要捕获更多分组，则需要根据实际情况进行修改。

**注意**: 
1. 不要直接[[ 字符串 =~ 正则表达式 ]] && echo ${BASH_REMATCH[@]}这样把字符串和正则直接放在中括号里，这样会一直没有匹配
2. 正则表达式不能使用引号包围
2. 这个是bash的正则匹配，直接在zsh终端下，可能会不生效，要先把字符串和正则都设置到两个变量，然后在引用变量来进行匹配
3. 方式一，字符串放到变量, tmp_str="abc123def"; [[ $tmp_str =~ .* ]] && echo ${BASH_REMATCH[@]}
4. 方式二，两个都放到变量, tmp_str="abc123def";re='.*'; [[ $tmp_str =~ $re ]] && echo ${BASH_REMATCH[@]}
**Example Function:**

```sh
regex() {
    # Usage: regex "string" "regex"
    [[ $1 =~ $2 ]] && printf '%s\n' "${BASH_REMATCH[1]}"
}
```

**Example Usage:**

```shell
$ # Trim leading white-space.
$ regex '    hello' '^\s*(.*)'
hello

$ # Validate a hex color.
$ regex "#FFFFFF" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
#FFFFFF

$ # Validate a hex color (invalid).
$ regex "red" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
# no output (invalid)
```

**Example Usage in script:**

```shell
is_hex_color() {
    if [[ $1 =~ ^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$ ]]; then
        printf '%s\n' "${BASH_REMATCH[1]}"
    else
        printf '%s\n' "error: $1 is an invalid color."
        return 1
    fi
}

read -r color
is_hex_color "$color" || color="#FFFFFF"

# Do stuff.
```

## Split 分割字符串

This is an alternative to `cut`, `awk` and other tools.

**Example Function:**

```sh
split() {
   # Usage: split "string" "delimiter"
   IFS=$'\n' read -d "" -ra arr <<< "${1//$2/$'\n'}"
   printf '%s\n' "${arr[@]}"
}
```

**Example Usage:**

```shell
$ split "apples,oranges,pears,grapes" ","
apples
oranges
pears
grapes

$ split "1, 2, 3, 4, 5" ", "
1
2
3
4
5

# Multi char delimiters work too!
$ split "hello---world---my---name---is---john" "---"
hello
world
my
name
is
john
```

## 转小写

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
lower() {
    # Usage: lower "string"
    printf '%s\n' "${1,,}"
}
```

**Example Usage:**

```shell
$ lower "HELLO"
hello

$ lower "HeLlO"
hello

$ lower "hello"
hello
```

## 转大写

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
upper() {
    # Usage: upper "string"
    printf '%s\n' "${1^^}"
}
```

**Example Usage:**

```shell
$ upper "hello"
HELLO

$ upper "HeLlO"
HELLO

$ upper "HELLO"
HELLO
```

## 去掉字符串里面的引号

**Example Function:**

```sh
trim_quotes() {
    # Usage: trim_quotes "string"
    : "${1//\'}"
    printf '%s\n' "${_//\"}"
}
```

**Example Usage:**

```shell
$ var="'Hello', \"World\""
$ trim_quotes "$var"
Hello, World
```

## 从字符串中删掉所有匹配到的内容

**Example Function:**

```sh
strip_all() {
    # Usage: strip_all "string" "pattern"
    printf '%s\n' "${1//$2}"
}
```

**Example Usage:**

```shell
$ strip_all "The Quick Brown Fox" "[aeiou]"
Th Qck Brwn Fx

$ strip_all "The Quick Brown Fox" "[[:space:]]"
TheQuickBrownFox

$ strip_all "The Quick Brown Fox" "Quick "
The Brown Fox
```

## 从字符串中删掉第一个匹配到的内容

**Example Function:**

```sh
strip() {
    # Usage: strip "string" "pattern"
    printf '%s\n' "${1/$2}"
}
```

**Example Usage:**

```shell
$ strip "The Quick Brown Fox" "[aeiou]"
Th Quick Brown Fox

$ strip "The Quick Brown Fox" "[[:space:]]"
TheQuick Brown Fox
```

## 从字符串开头删除匹配到的内容

**Example Function:**

```sh
lstrip() {
    # Usage: lstrip "string" "pattern"
    printf '%s\n' "${1##$2}"
}
```

**Example Usage:**

```shell
$ lstrip "The Quick Brown Fox" "The "
Quick Brown Fox
```

## 从字符串的结尾删除匹配到的内容

**Example Function:**

```sh
rstrip() {
    # Usage: rstrip "string" "pattern"
    printf '%s\n' "${1%%$2}"
}
```

**Example Usage:**

```shell
$ rstrip "The Quick Brown Fox" " Fox"
The Quick Brown
```

## url编码

**Example Function:**

```sh
urlencode() {
    # Usage: urlencode "string"
    local LC_ALL=C
    for (( i = 0; i < ${#1}; i++ )); do
        : "${1:i:1}"
        case "$_" in
            [a-zA-Z0-9.~_-])
                printf '%s' "$_"
            ;;

            *)
                printf '%%%02X' "'$_"
            ;;
        esac
    done
    printf '\n'
}
```

**Example Usage:**

```shell
$ urlencode "https://github.com/dylanaraps/pure-bash-bible"
https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible
```

## url解码

**Example Function:**

```sh
urldecode() {
    # Usage: urldecode "string"
    : "${1//+/ }"
    printf '%b\n' "${_//%/\\x}"
}
```

**Example Usage:**

```shell
$ urldecode "https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible"
https://github.com/dylanaraps/pure-bash-bible
```

## 是否包含某子串

**Using a test:**

```shell
if [[ $var == *sub_string* ]]; then
    printf '%s\n' "sub_string is in var."
fi

# Inverse (substring not in string).
if [[ $var != *sub_string* ]]; then
    printf '%s\n' "sub_string is not in var."
fi

# This works for arrays too!
if [[ ${arr[*]} == *sub_string* ]]; then
    printf '%s\n' "sub_string is in array."
fi
```

**Using a case statement:**

```shell
case "$var" in
    *sub_string*)
        # Do stuff
    ;;

    *sub_string2*)
        # Do more stuff
    ;;

    *)
        # Else
    ;;
esac
```

## 是否以某子串开头

```shell
if [[ $var == sub_string* ]]; then
    printf '%s\n' "var starts with sub_string."
fi

# Inverse (var does not start with sub_string).
if [[ $var != sub_string* ]]; then
    printf '%s\n' "var does not start with sub_string."
fi
```

## 是否以某子串结尾

```shell
if [[ $var == *sub_string ]]; then
    printf '%s\n' "var ends with sub_string."
fi

# Inverse (var does not end with sub_string).
if [[ $var != *sub_string ]]; then
    printf '%s\n' "var does not end with sub_string."
fi
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 数组

## Reverse 一个数组

Enabling `extdebug` allows access to the `BASH_ARGV` array which stores
the current function’s arguments in reverse.

**Example Function:**

```sh
reverse_array() {
    # Usage: reverse_array "array"
    shopt -s extdebug
    f()(printf '%s\n' "${BASH_ARGV[@]}"); f "$@"
    shopt -u extdebug
}
```

**Example Usage:**

```shell
$ reverse_array 1 2 3 4 5
5
4
3
2
1

$ arr=(red blue green)
$ reverse_array "${arr[@]}"
green
blue
red
```

## 去重，得到set

Create a temporary associative array. When setting associative array
values and a duplicate assignment occurs, bash overwrites the key. This
allows us to effectively remove array duplicates.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
remove_array_dups() {
    # Usage: remove_array_dups "array"
    declare -A tmp_array

    for i in "$@"; do
        [[ $i ]] && IFS=" " tmp_array["${i:- }"]=1
    done

    printf '%s\n' "${!tmp_array[@]}"
}
```

**Example Usage:**

```shell
$ remove_array_dups 1 1 2 2 3 3 3 3 3 4 4 4 4 4 5 5 5 5 5 5
1
2
3
4
5

$ arr=(red red green blue blue)
$ remove_array_dups "${arr[@]}"
red
green
blue
```

## 从数组随机取一个元素

**Example Function:**

```sh
random_array_element() {
    # Usage: random_array_element "array"
    local arr=("$@")
    printf '%s\n' "${arr[RANDOM % $#]}"
}
```

**Example Usage:**

```shell
$ array=(red green blue yellow brown)
$ random_array_element "${array[@]}"
yellow

# Multiple arguments can also be passed.
$ random_array_element 1 2 3 4 5 6 7
3
```

## 打圈地循环数组

Each time the `printf` is called, the next array element is printed. When
the print hits the last array element it starts from the first element
again.

```sh
arr=(a b c d)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```

## Toggle 切换两个值

This works the same as above, this is just a different use case.

```sh
arr=(true false)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 循环

## 遍历数字范围

Alternative to `seq`.

```shell
# Loop from 0-100 (no variable support).
for i in {0..100}; do
    printf '%s\n' "$i"
done
```

## 普通循环0-i

Alternative to `seq`.

```shell
# Loop from 0-VAR.
VAR=50
for ((i=0;i<=VAR;i++)); do
    printf '%s\n' "$i"
done
```

## 遍历数组元素

```shell
arr=(apples oranges tomatoes)

# Just elements.
for element in "${arr[@]}"; do
    printf '%s\n' "$element"
done
```

## 以index来遍历数组

```shell
arr=(apples oranges tomatoes)

# Elements and index.
for i in "${!arr[@]}"; do
    printf '%s\n' "${arr[i]}"
done

# Alternative method.
for ((i=0;i<${#arr[@]};i++)); do
    printf '%s\n' "${arr[i]}"
done
```

## 一行一行地遍历文件内容

```shell
while read -r line; do
    printf '%s\n' "$line"
done < "file"
```

## 遍历文件和目录

Don’t use `ls`.

```shell
# Greedy example.
for file in *; do
    printf '%s\n' "$file"
done

# PNG files in dir.
for file in ~/Pictures/*.png; do
    printf '%s\n' "$file"
done

# Iterate over directories.
for dir in ~/Downloads/*/; do
    printf '%s\n' "$dir"
done

# Brace Expansion.
for file in /path/to/parentdir/{file1,file2,subdir/file3}; do
    printf '%s\n' "$file"
done

# Iterate recursively.
shopt -s globstar
for file in ~/Pictures/**/*; do
    printf '%s\n' "$file"
done
shopt -u globstar
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 文件处理

**CAVEAT:** `bash` does not handle binary data properly in versions `< 4.4`.

## 读取文件内容为一个字符串

Alternative to the `cat` command.

```shell
file_data="$(<"file")"
```

## 读取文件内容到数组，一行一个元素 (*by line*)

Alternative to the `cat` command.

```shell
# Bash <4
IFS=$'\n' read -d "" -ra file_data < "file"

# Bash 4+
mapfile -t file_data < "file"
```

## 获取文件前N行

Alternative to the `head` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
head() {
    # Usage: head "n" "file"
    mapfile -tn "$1" line < "$2"
    printf '%s\n' "${line[@]}"
}
```

**Example Usage:**

```shell
$ head 2 ~/.bashrc
# Prompt
PS1='➜ '

$ head 1 ~/.bashrc
# Prompt
```

## 获取文件后N行

Alternative to the `tail` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
tail() {
    # Usage: tail "n" "file"
    mapfile -tn 0 line < "$2"
    printf '%s\n' "${line[@]: -$1}"
}
```

**Example Usage:**

```shell
$ tail 2 ~/.bashrc
# Enable tmux.
# [[ -z "$TMUX"  ]] && exec tmux

$ tail 1 ~/.bashrc
# [[ -z "$TMUX"  ]] && exec tmux
```

## 获取文件行数

Alternative to `wc -l`.

**Example Function (bash 4):**

```sh
lines() {
    # Usage: lines "file"
    mapfile -tn 0 lines < "$1"
    printf '%s\n' "${#lines[@]}"
}
```

**Example Function (bash 3):**

This method uses less memory than the `mapfile` method and works in `bash` 3 but it is slower for bigger files.

```sh
lines_loop() {
    # Usage: lines_loop "file"
    count=0
    while IFS= read -r _; do
        ((count++))
    done < "$1"
    printf '%s\n' "$count"
}
```

**Example Usage:**

```shell
$ lines ~/.bashrc
48

$ lines_loop ~/.bashrc
48
```

## 获取目录下有多少个东西（文件或目录）

This works by passing the output of the glob to the function and then counting the number of arguments.

**Example Function:**

```sh
count() {
    # Usage: count /path/to/dir/*
    #        count /path/to/dir/*/
    printf '%s\n' "$#"
}
```

**Example Usage:**

```shell
# Count all files in dir.
$ count ~/Downloads/*
232

# Count all dirs in dir.
$ count ~/Downloads/*/
45

# Count all jpg files in dir.
$ count ~/Pictures/*.jpg
64
```

## 创建空文件

Alternative to `touch`.

```shell
# Shortest.
>file

# Longer alternatives:
:>file
echo -n >file
printf '' >file
```

## 提取两行标记之间的内容

**Example Function:**

```sh
extract() {
    # Usage: extract file "opening marker" "closing marker"
    while IFS=$'\n' read -r line; do
        [[ $extract && $line != "$3" ]] &&
            printf '%s\n' "$line"

        [[ $line == "$2" ]] && extract=1
        [[ $line == "$3" ]] && extract=
    done < "$1"
}
```

**Example Usage:**

```shell
# Extract code blocks from MarkDown file.
$ extract ~/projects/pure-bash/README.md '```sh' '```'
# Output here...
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 文件路径

## 获取所在目录

Alternative to the `dirname` command.

**Example Function:**

```sh
dirname() {
    # Usage: dirname "path"
    printf '%s\n' "${1%/*}/"
}
```

**Example Usage:**

```shell
$ dirname ~/Pictures/Wallpapers/1.jpg
/home/black/Pictures/Wallpapers/

$ dirname ~/Pictures/Downloads/
/home/black/Pictures/
```

## 获取base-name，即去掉路径的目录部分

Alternative to the `basename` command.

**Example Function:**

```sh
basename() {
    # Usage: basename "path"
    : "${1%/}"
    printf '%s\n' "${_##*/}"
}
```

**Example Usage:**

```shell
$ basename ~/Pictures/Wallpapers/1.jpg
1.jpg

$ basename ~/Pictures/Downloads/
Downloads
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 变量

## 嵌套变量，动态变量

```shell
$ hello_world="value"

# Create the variable name.
$ var="world"
$ ref="hello_$var"

# Print the value of the variable name stored in 'hello_$var'.
$ printf '%s\n' "${!ref}"
value
```

Alternatively, on `bash` 4.3+:

```shell
$ hello_world="value"
$ var="world"

# Declare a nameref.
$ declare -n ref=hello_$var

$ printf '%s\n' "$ref"
value
```

## 动态变量名，即基于变量来定义另外一个变量

```shell
$ var="world"
$ declare "hello_$var=value"
$ printf '%s\n' "$hello_world"
value
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 转义字符串

Contrary to popular belief, there is no issue in utilizing raw escape sequences. Using `tput` abstracts the same ANSI sequences as if printed manually. Worse still, `tput` is not actually portable. There are a number of `tput` variants each with different commands and syntaxes (*try `tput setaf 3` on a FreeBSD system*). Raw sequences are fine.

## 文本颜色

**NOTE:** Sequences requiring RGB values only work in True-Color Terminal Emulators.

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[38;5;<NUM>m` | 前景颜色. | `0-255`
| `\e[48;5;<NUM>m` | 背景颜色. | `0-255`
| `\e[38;2;<R>;<G>;<B>m` | 用RGB设置前景颜色. | `R`, `G`, `B`
| `\e[48;2;<R>;<G>;<B>m` | 用RGB设置背景颜色. | `R`, `G`, `B`

## 文本属性

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[m`  | 重置.
| `\e[1m` | 粗体字. |
| `\e[2m` | Faint text. |
| `\e[3m` | 斜体字. |
| `\e[4m` | 下划线. |
| `\e[5m` | Slow blink. |
| `\e[7m` | Swap foreground and background colors. |

## 光标移动

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[<LINE>;<COLUMN>H` | 移动光标到绝对位置. | `line`, `column`
| `\e[H` | 移动光标到初始home位置 (`0,0`). |
| `\e[<NUM>A` | 光标向上N行. | `num`
| `\e[<NUM>B` | 光标向下N行. | `num`
| `\e[<NUM>C` | 光标向右N列. | `num`
| `\e[<NUM>D` | 光标向左N列. | `num`
| `\e[s` | 保存光标位置. |
| `\e[u` | 恢复光标位置. |

## 删除文本

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[K` | 删除光标位置到行尾.
| `\e[1K` | 删除光标位置到行首.
| `\e[2K` | 删除整行.
| `\e[J` | 删除光标所在行到屏幕底部.
| `\e[1J` | 删除光标所在行到屏幕顶部.
| `\e[2J` | 清屏.
| `\e[2J\e[H` | 清屏并光标回到初始位置 `0,0`.


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 变量扩展

## Indirection

| Parameter | What does it do? |
| --------- | ---------------- |
| `${!VAR}` | Access a variable based on the value of `VAR`.
| `${!VAR*}` | Expand to `IFS` separated list of variable names starting with `VAR`. |
| `${!VAR@}` | Expand to `IFS` separated list of variable names starting with `VAR`. If double-quoted, each variable name expands to a separate word. |


## 替换
**NOTE:** #在键盘左边，%在键盘右边，一个#短匹配，两个#长匹配

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR#PATTERN}` | 从左边删除最短匹配. |
| `${VAR##PATTERN}` | 从左边删除最长匹配. |
| `${VAR%PATTERN}` | 从右边删除最短匹配. |
| `${VAR%%PATTERN}` | 从左边删除最长匹配. |
| `${VAR/PATTERN/REPLACE}` | 替换第一个匹配项.|
| `${VAR//PATTERN/REPLACE}` | 替换所有匹配项.|
| `${VAR/PATTERN}` | 删除第一个匹配项.|
| `${VAR//PATTERN}` | 删除所有匹配项.|

## 长度

| Parameter | What does it do? |
| --------- | ---------------- |
| `${#VAR}` | 字符串长度.
| `${#ARR[@]}` | 数组长度.

## 扩展

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR:OFFSET}` | 删除前`N`个字符.
| `${VAR:OFFSET:LENGTH}` | Get substring from `N` character to `N` character. <br> (`${VAR:10:10}`: Get sub-string from char `10` to char `20`)
| `${VAR:: OFFSET}` | 获取前`N`个字符.
| `${VAR:: -OFFSET}` | 删除后`N`个字符.
| `${VAR: -OFFSET}` | 获取后`N`个字符.
| `${VAR:OFFSET:-OFFSET}` | Cut first `N` chars and last `N` chars. | `bash 4.2+` |

## 大小写转换

| Parameter | What does it do? | CAVEAT |
| --------- | ---------------- | ------ |
| `${VAR^}` | 首字母转大写. | `bash 4+` |
| `${VAR^^}` | 转大写. | `bash 4+` |
| `${VAR,}` | 首字母小写. | `bash 4+` |
| `${VAR,,}` | 转小写. | `bash 4+` |


## 默认值
**NOTE:** 
1. 有=的两个才会设置VAR的值
2. 长（有:） <----对应----> 长（既空也未定义）,短（无:）<----对应---->短（只有未定义）
3. 有+的取反
| Parameter | What does it do? |记忆|
| --------- | ---------------- |-----------------------|
| `${VAR:-STRING}` | `VAR` 空或未定义, 用 `STRING`.| 长
| `${VAR-STRING}` | `VAR` 未定义, 用 `STRING`.| 短
| `${VAR:=STRING}` | `VAR` 空或未定义, 设置 `VAR` 为 `STRING`.|长，有=所以设值
| `${VAR=STRING}` | `VAR` 未定义, 设置 `VAR` 为 `STRING`.|短，有=所以设值
| `${VAR:+STRING}` | `VAR` 不为空（!空或未定义）, 用 `STRING`.|长，有+所以取反!
| `${VAR+STRING}` | `VAR` 已定义(!未定义）, 用 `STRING`.|短，有+所以取反!
| `${VAR:?STRING}` | 空或未定义，显示err_msg.|长
| `${VAR?STRING}` | 未定义，显示err_msg.|短


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# BRACE EXPANSION

## 范围{a..b}

```shell
# Syntax: {<START>..<END>}

# Print numbers 1-100.
echo {1..100}

# Print range of floats.
echo 1.{1..9}

# Print chars a-z.
echo {a..z}
echo {A..Z}

# Nesting.
echo {A..Z}{0..9}

# Print zero-padded numbers.
# CAVEAT: bash 4+
echo {01..100}

# Change increment amount.
# Syntax: {<START>..<END>..<INCREMENT>}
# CAVEAT: bash 4+
echo {1..10..2} # Increment by 2.
```

## 列表{a,b}

```shell
echo {apples,oranges,pears,grapes}

# Example Usage:
# Remove dirs Movies, Music and ISOS from ~/Downloads/.
rm -rf ~/Downloads/{Movies,Music,ISOS}
```

<!-- CHAPTER END -->


<!-- CHAPTER START -->

# 条件表达式test

## 文件条件语句

| Expression | Value  | What does it do? |
| ---------- | ------ | ---------------- |
| `-a`       | `file` | 文件存在.
| `-b`       | `file` | If file exists and is a block special file.
| `-c`       | `file` | If file exists and is a character special file.
| `-d`       | `file` | 文件存在并且是目录.
| `-e`       | `file` | 文件存在.
| `-f`       | `file` | If file exists and is a regular file.
| `-g`       | `file` | If file exists and its set-group-id bit is set.
| `-h`       | `file` | I文件存在并且是一个软连接.
| `-k`       | `file` | If file exists and its sticky-bit is set
| `-p`       | `file` | If file exists and is a named pipe (*FIFO*).
| `-r`       | `file` | 文件存在并且可读.
| `-s`       | `file` | If file exists and its size is greater than zero.
| `-t`       | `fd`   | If file descriptor is open and refers to a terminal.
| `-u`       | `file` | If file exists and its set-user-id bit is set.
| `-w`       | `file` | 文件存在并且可写.
| `-x`       | `file` | 文件存在并且可执行.
| `-G`       | `file` | If file exists and is owned by the effective group ID.
| `-L`       | `file` | 文件存在并且是一个软连接.
| `-N`       | `file` | If file exists and has been modified since last read.
| `-O`       | `file` | If file exists and is owned by the effective user ID.
| `-S`       | `file` | 文件存在并且是一个socket文件.

## 文件比较

| Expression | What does it do? |
| ---------- | ---------------- |
| `file -ef file2` | If both files refer to the same inode and device numbers.
| `file -nt file2` | If `file` is newer than `file2` (*uses modification time*) or `file` exists and `file2` does not.
| `file -ot file2` | If `file` is older than `file2` (*uses modification time*) or `file2` exists and `file` does not.

## 变量条件语句

| Expression | Value | What does it do? |
| ---------- | ----- | ---------------- |
| `-o`       | `opt` | If shell option is enabled.
| `-v`       | `var` | If variable has a value assigned.
| `-R`       | `var` | If variable is a name reference.
| `-z`       | `var` | 字符串长度为零.
| `-n`       | `var` | 字符串长度不为零.

## 变量比较

| Expression | What does it do? |
| ---------- | ---------------- |
| `var = var2` | Equal to.
| `var == var2` | Equal to (*synonym for `=`*).
| `var != var2` | Not equal to.
| `var < var2` | Less than (*in ASCII alphabetical order.*)
| `var > var2` | Greater than (*in ASCII alphabetical order.*)

<!-- CHAPTER END -->

<!-- CHAPTER START -->

# 算术操作

## 赋值

| Operators | What does it do? |
| --------- | ---------------- |
| `=`       | Initialize or change the value of a variable.

## 算数

| Operators | What does it do? |
| --------- | ---------------- |
| `+` | Addition
| `-` | Subtraction
| `*` | Multiplication
| `/` | Division
| `**` | Exponentiation
| `%` | Modulo
| `+=` | Plus-Equal (*Increment a variable.*)
| `-=` | Minus-Equal (*Decrement a variable.*)
| `*=` | Times-Equal (*Multiply a variable.*)
| `/=` | Slash-Equal (*Divide a variable.*)
| `%=` | Mod-Equal (*Remainder of dividing a variable.*)

## 位运算

| Operators | What does it do? |
| --------- | ---------------- |
| `<<` | Bitwise Left Shift
| `<<=` | Left-Shift-Equal
| `>>` | Bitwise Right Shift
| `>>=` | Right-Shift-Equal
| `&` | Bitwise AND
| `&=` | Bitwise AND-Equal
| `\|` | Bitwise OR
| `\|=` | Bitwise OR-Equal
| `~` | Bitwise NOT
| `^` | Bitwise XOR
| `^=` | Bitwise XOR-Equal

## 逻辑

| Operators | What does it do? |
| --------- | ---------------- |
| `!` | NOT
| `&&` | AND
| `\|\|` | OR

## 杂项

| Operators | What does it do? | Example |
| --------- | ---------------- | ------- |
| `,` | Comma Separator | `((a=1,b=2,c=3))`


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 计算

## 简单计算

```shell
# Simple math
((var=1+2))

# Decrement/Increment variable
((var++))
((var--))
((var+=1))
((var-=1))

# Using variables
((var=var2*arr[2]))
```

## 三目表达式

```shell
# Set the value of var to var2 if var2 is greater than var.
# var: variable to set.
# var2>var: Condition to test.
# ?var2: If the test succeeds.
# :var: If the test fails.
((var=var2>var?var2:var))
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 捕获信息

Traps allow a script to execute code on various signals. In [pxltrm](https://github.com/dylanaraps/pxltrm) (*a pixel art editor written in bash*)  traps are used to redraw the user interface on window resize. Another use case is cleaning up temporary files on script exit.

Traps should be added near the start of scripts so any early errors are also caught.

**NOTE:** For a full list of signals, see `trap -l`.


## 脚本结束时干些事情

```shell
# Clear screen on script exit.
trap 'printf \\e[2J\\e[H\\e[m' EXIT
```

## 忽略终端打断(CTRL+C, SIGINT)

```shell
trap '' INT
```

## React to window resize

```shell
# Call a function on window resize.
trap 'code_here' SIGWINCH
```

## 每个命令之前干些事情

```shell
trap 'code_here' DEBUG
```

## 方法执行后干些事情

```shell
trap 'code_here' RETURN
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# PERFORMANCE

## 关闭 Unicode

If unicode is not required, it can be disabled for a performance increase. Results may vary however there have been noticeable improvements in [neofetch](https://github.com/dylanaraps/neofetch) and other programs.

```shell
# Disable unicode.
LC_ALL=C
LANG=C
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 旧语法

## Shebang

Use `#!/usr/bin/env bash` instead of `#!/bin/bash`.

- The former searches the user's `PATH` to find the `bash` binary.
- The latter assumes it is always installed to `/bin/` which can cause issues.

```shell
# Right:

    #!/usr/bin/env bash

# Wrong:

    #!/bin/bash
```

## 命令替换

Use `$()` instead of `` ` ` ``.

```shell
# Right.
var="$(command)"

# Wrong.
var=`command`

# $() can easily be nested whereas `` cannot.
var="$(command "$(command)")"
```

## 方法的定义

Do not use the `function` keyword, it reduces compatibility with older versions of `bash`.

```shell
# Right.
do_something() {
    # ...
}

# Wrong.
function do_something() {
    # ...
}
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 内置变量

## `bash`二进制路径

```shell
"$BASH"
```

## 当前运行到`bash`版本

```shell
# As a string.
"$BASH_VERSION"

# As an array.
"${BASH_VERSINFO[@]}"
```

## 用户首选到编辑器

```shell
"$EDITOR" "$file"

# NOTE: This variable may be empty, set a fallback value.
"${EDITOR:-vi}" "$file"
```

## 获取方法的名字

```shell
# Current function.
"${FUNCNAME[0]}"

# Parent function.
"${FUNCNAME[1]}"

# So on and so forth.
"${FUNCNAME[2]}"
"${FUNCNAME[3]}"

# All functions including parents.
"${FUNCNAME[@]}"
```

## 获取主机名hostname

```shell
"$HOSTNAME"

# NOTE: This variable may be empty.
# Optionally set a fallback to the hostname command.
"${HOSTNAME:-$(hostname)}"
```

## 获取系统架构

```shell
"$HOSTTYPE"
```

## 获取系统名称

This can be used to add conditional support for different Operating
Systems without needing to call `uname`.

```shell
"$OSTYPE"
```

## 获取当前工作目录pwd

This is an alternative to the `pwd` built-in.

```shell
"$PWD"
```

## 获取脚本运行了多长时间

```shell
"$SECONDS"
```

## 获取随机整数0-32767

Each time `$RANDOM` is used, a different integer between `0` and `32767` is returned. This variable should not be used for anything related to security (*this includes encryption keys etc*).


```shell
"$RANDOM"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 终端信息

## 在脚本里获取窗口大小，几行几列

This is handy when writing scripts in pure bash and `stty`/`tput` can’t be
called.

**Example Function:**

```sh
get_term_size() {
    # Usage: get_term_size

    # (:;:) is a micro sleep to ensure the variables are
    # exported immediately.
    shopt -s checkwinsize; (:;:)
    printf '%s\n' "$LINES $COLUMNS"
}
```

**Example Usage:**

```shell
# Output: LINES COLUMNS
$ get_term_size
15 55
```

## 获取终端像素

**CAVEAT**: This does not work in some terminal emulators.

**Example Function:**

```sh
get_window_size() {
    # Usage: get_window_size
    printf '%b' "${TMUX:+\\ePtmux;\\e}\\e[14t${TMUX:+\\e\\\\}"
    IFS=';t' read -d t -t 0.05 -sra term_size
    printf '%s\n' "${term_size[1]}x${term_size[2]}"
}
```

**Example Usage:**

```shell
# Output: WIDTHxHEIGHT
$ get_window_size
1200x800

# Output (fail):
$ get_window_size
x
```

## 获取光标位置

This is useful when creating a TUI in pure bash.

**Example Function:**

```sh
get_cursor_pos() {
    # Usage: get_cursor_pos
    IFS='[;' read -p $'\e[6n' -d R -rs _ y x _
    printf '%s\n' "$x $y"
}
```

**Example Usage:**

```shell
# Output: X Y
$ get_cursor_pos
1 8
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 转换

## 哈希颜色 转 RGB

**Example Function:**

```sh
hex_to_rgb() {
    # Usage: hex_to_rgb "#FFFFFF"
    #        hex_to_rgb "000000"
    : "${1/\#}"
    ((r=16#${_:0:2},g=16#${_:2:2},b=16#${_:4:2}))
    printf '%s\n' "$r $g $b"
}
```

**Example Usage:**

```shell
$ hex_to_rgb "#FFFFFF"
255 255 255
```

## RGB 转 哈希颜色

**Example Function:**

```sh
rgb_to_hex() {
    # Usage: rgb_to_hex "r" "g" "b"
    printf '#%02x%02x%02x\n' "$1" "$2" "$3"
}
```

**Example Usage:**

```shell
$ rgb_to_hex "255" "255" "255"
#FFFFFF
```


# 更简单的代码写法

## 更短的`for`语法

```shell
# Tiny C Style.
for((;i++<10;)){ echo "$i";}

# Undocumented method.
for i in {1..10};{ echo "$i";}

# Expansion.
for i in {1..10}; do echo "$i"; done

# C Style.
for((i=0;i<=10;i++)); do echo "$i"; done
```

## 更短的无限循环

```shell
# Normal method
while :; do echo hi; done

# Shorter
for((;;)){ echo hi;}
```

## 更短的方法定义

```shell
# Normal method
f(){ echo hi;}

# Using a subshell
f()(echo hi)

# Using arithmetic
# This can be used to assign integer values.
# Example: f a=1
#          f a++
f()(($1))

# Using tests, loops etc.
# NOTE: ‘while’, ‘until’, ‘case’, ‘(())’, ‘[[]]’ can also be used.
f()if true; then echo "$1"; fi
f()for i in "$@"; do echo "$i"; done
```

## 更短的 `if` 语法

```shell
# One line
# Note: The 3rd statement may run when the 1st is true
[[ $var == hello ]] && echo hi || echo bye
[[ $var == hello ]] && { echo hi; echo there; } || echo bye

# Multi line (no else, single statement)
# Note: The exit status may not be the same as with an if statement
[[ $var == hello ]] &&
    echo hi

# Multi line (no else)
[[ $var == hello ]] && {
    echo hi
    # ...
}
```

## 更简单的`switch`设置变量

The `:` built-in can be used to avoid repeating `variable=` in a case statement. The `$_` variable stores the last argument of the last command. `:` always succeeds so it can be used to store the variable value.

```shell
# Modified snippet from Neofetch.
case "$OSTYPE" in
    "darwin"*)
        : "MacOS"
    ;;

    "linux"*)
        : "Linux"
    ;;

    *"bsd"* | "dragonfly" | "bitrig")
        : "BSD"
    ;;

    "cygwin" | "msys" | "win32")
        : "Windows"
    ;;

    *)
        printf '%s\n' "Unknown OS detected, aborting..." >&2
        exit 1
    ;;
esac

# Finally, set the variable.
os="$_"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# 其他

## 用`read`代替`sleep`命令

Surprisingly, `sleep` is an external command and not a `bash` built-in.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
read_sleep() {
    # Usage: sleep 1
    #        sleep 0.2
    read -rst "${1:-1}" -N 999
}
```

**Example Usage:**

```shell
read_sleep 1
read_sleep 0.1
read_sleep 30
```

## 程序是否在环境变量PATH的目录里, 程序是否安装

```shell
# There are 3 ways to do this and either one can be used.
type -p executable_name &>/dev/null
hash executable_name &>/dev/null
command -v executable_name &>/dev/null

# As a test.
if type -p executable_name &>/dev/null; then
    # Program is in PATH.
fi

# Inverse.
if ! type -p executable_name &>/dev/null; then
    # Program is not in PATH.
fi

# Example (Exit early if program is not installed).
if ! type -p convert &>/dev/null; then
    printf '%s\n' "error: convert is not installed, exiting..."
    exit 1
fi
```

## 利用printf获取当前时间

Bash’s `printf` has a built-in method of getting the date which can be used in place of the `date` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
date() {
    # Usage: date "format"
    # See: 'man strftime' for format.
    printf "%($1)T\\n" "-1"
}
```

**Example Usage:**

```shell
# Using above function.
$ date "%a %d %b  - %l:%M %p"
Fri 15 Jun  - 10:00 AM

# Using printf directly.
$ printf '%(%a %d %b  - %l:%M %p)T\n' "-1"
Fri 15 Jun  - 10:00 AM

# Assigning a variable using printf.
$ printf -v date '%(%a %d %b  - %l:%M %p)T\n' '-1'
$ printf '%s\n' "$date"
Fri 15 Jun  - 10:00 AM
```

## 获取当前用户的用户名

**CAVEAT:** Requires `bash` 4.4+

```shell
$ : \\u
# Expand the parameter as if it were a prompt string.
$ printf '%s\n' "${_@P}"
black
```

## 生成 UUID V4

**CAVEAT**: The generated value is not cryptographically secure.

**Example Function:**

```sh
uuid() {
    # Usage: uuid
    C="89ab"

    for ((N=0;N<16;++N)); do
        B="$((RANDOM%256))"

        case "$N" in
            6)  printf '4%x' "$((B%16))" ;;
            8)  printf '%c%x' "${C:$RANDOM%${#C}:1}" "$((B%16))" ;;

            3|5|7|9)
                printf '%02x-' "$B"
            ;;

            *)
                printf '%02x' "$B"
            ;;
        esac
    done

    printf '\n'
}
```

**Example Usage:**

```shell
$ uuid
d5b6c731-1310-4c24-9fe3-55d556d44374
```

## 进度条

This is a simple way of drawing progress bars without needing a for loop
in the function itself.

**Example Function:**

```sh
bar() {
    # Usage: bar 1 10
    #            ^----- Elapsed Percentage (0-100).
    #               ^-- Total length in chars.
    ((elapsed=$1*$2/100))

    # Create the bar with spaces.
    printf -v prog  "%${elapsed}s"
    printf -v total "%$(($2-elapsed))s"

    printf '%s\r' "[${prog// /-}${total}]"
}
```

**Example Usage:**

```shell
for ((i=0;i<=100;i++)); do
    # Pure bash micro sleeps (for the example).
    (:;:) && (:;:) && (:;:) && (:;:) && (:;:)

    # Print the bar.
    bar "$i" "10"
done

printf '\n'
```

## 获取脚本的所有方法列表

```sh
get_functions() {
    # Usage: get_functions
    IFS=$'\n' read -d "" -ra functions < <(declare -F)
    printf '%s\n' "${functions[@]//declare -f }"
}
```

## Bypass shell aliases

```shell
# alias
ls

# command
# shellcheck disable=SC1001
\ls
```

## Bypass shell functions

```shell
# function
ls

# command
command ls
```

## 后台运行

This will run the given command and keep it running, even after the terminal or SSH connection is terminated. All output is ignored.

```sh
bkr() {
    (nohup "$@" &>/dev/null &)
}

bkr ./some_script.sh # some_script.sh is now running in the background
```

<!-- CHAPTER END -->

# AFTERWORD

Thanks for reading! If this bible helped you in any way and you'd like to give back, consider donating. Donations give me the time to make this the best resource possible. Can't donate? That's OK, star the repo and share it with your friends!

<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=V7QNJNKS3WYVS"><img src="https://img.shields.io/badge/donate-paypal-yellow.svg"></a> <a href="https://www.patreon.com/dyla"><img src="https://img.shields.io/badge/donate-patreon-yellow.svg"> </a><a href="https://liberapay.com/2211/"><img src="https://img.shields.io/badge/donate-liberapay-yellow.svg"></a>


Rock on. 🤘

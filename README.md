# litdate

一个非常简单的时间处理工具

## 目标

与语言无关的时间处理工具，本身没有多语言支持但可以方便的结合中文使用，使用客户端的时区

## 安装

现在可以通过 npm 安装和使用 litdate 了。

```
npm install @xiongliding/litdate
```

### node

```
const litdate = require('litdate');
```

### webpack 等

```
import litdate from 'litdate';
```

## 用法

```
var ld = litdate(); // 当前时间
ld.Y // 2017;
ld.format('Y-m-d H:i:s'); // 2017-12-05 22:16:07

var ld20170101 = litdate(new Date(2017, 0, 1, 22, 16, 7)); // 传入 Date 对象
ld20170101.format('y年n月j日 G时I分S秒'); // 17年1月1日 22时16分7秒
```

更多用法可参考 test.js 中的测试用例。

## 属性与方法

内容基本参照了 php 的日期页面，但由于不需要支持语言和时区，把 Z I S e 的用途做了改变。

无前导 0 的为数值类型，前导 0 的为字符串类型。

| 属性 | 描述                                                             | 例子              | 备注               |
| ---- | ---------------------------------------------------------------- | ----------------- | ------------------ |
| 日   | ----                                                             | ----              | ----               |
| d    | 每月的几号，2 位数字，前导 0                                     | 01 到 31          |                    |
| j    | 每月的几号，无前导 0                                             | 1 到 31           |                    |
| N    | ISO-8601 周日历，每周第几天                                      | 1(周一)到 7(周日) |                    |
| w    | 每周第几天                                                       | 0(周日)到 6(周六) |                    |
| z    | 每年第几天(从 0 开始)                                            | 0 到 365          |                    |
| Z    | 每年第几天(从 1 开始)                                            | 1 到 366          | 变化               |
| 周   | ----                                                             | ----              | ----               |
| W    | ISO-8601 周日历第几周，每周从周一开始，前导 0                    | 01-53             |                    |
| e    | ISO-8601 周日历第几周，每周从周一开始，无前导 0                  | 1-53              | 变化               |
| 月   | ----                                                             | ----              | ----               |
| m    | 月份，前导 0                                                     | 01-12             |                    |
| n    | 月份，无前导 0                                                   | 1-12              |                    |
| t    | 本月有几天                                                       | 28-31             |                    |
| 年   | ----                                                             | ----              | ----               |
| L    | 是否闰年                                                         | 闰年 1，否则 0    |                    |
| o    | ISO-8601 周日历中的年份，一般和 Y 相同，年初和年尾的那周可能不同 | 例子：1999、2003  |                    |
| Y    | 年份，4 位数字                                                   | 例子：1999、2003  |                    |
| y    | 年份，2 位数字                                                   | 例子：99、03      |                    |
| 时间 | ----                                                             | ----              | ----               |
| a    | 午前午后                                                         | am pm             |                    |
| A    | 午前午后                                                         | AM PM             |                    |
| g    | 12 小时制，无前导 0                                              | 1 到 12           | 12 小时制没有 0 点 |
| G    | 24 小时制，无前导 0                                              | 0 到 23           |                    |
| h    | 12 小时制，前导 0                                                | 01 到 12          | 12 小时制没有 0 点 |
| H    | 24 小时制，前导 0                                                | 00 到 23          |                    |
| i    | 分，前导 0                                                       | 00 到 59          |                    |
| I    | 分，无前导 0                                                     | 0 到 59           | 变化               |
| s    | 秒，前导 0                                                       | 00 到 59          |                    |
| S    | 秒，无前导 0                                                     | 0 到 59           | 变化               |

| 方法   | 描述                                   | 例子                               |
| ------ | -------------------------------------- | ---------------------------------- |
| format | 将字符串中与属性名匹配的部分替换成数值 | ld.format('Y-m-d') => '2017-12-05' |

## 测试

```
npm run test
```

## 变更

现在主流环境都支持 ES6 语法，因此 litdate.js 也改用了新语法，尽管没什么实质性的提升。
新版本使用了 CommonJS 风格的 module.exports ，因为此方法兼容 node 和 webpack 等工具，但不能直接放到浏览器中运行。
等 node 默认支持 ES 标准的模块管理一段时间后，会将其改为 export 的形式。

早先的版本被更名为 litdate.legacy.js ，仍然使用了经典语法，方便直接在浏览器中引用。

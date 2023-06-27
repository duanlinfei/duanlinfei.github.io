---
layout: post
title: mysql舍入方法
categories: [未分类]
---

## 舍入方法
``` bash
# X:值 D:保留位数
# 四舍五入
ROUND(X,D)

# 取下限
TRUNCATE(X,D)

# 四舍五入，强制保留D位小数，整数部分超过三位的时候以逗号分割，并且返回的结果是string类型
FORMAT(X,D)
SELECT FORMAT(1001.3465,2); # 1,001.35

# 四舍五入，类型转换，相当于截取
CONVERT(VALUE,TYPE)
SELECT CONVERT(100.3465,DECIMAL(10,2)); # 100.35

# 四舍五入，类型转换，功能和CONVERT类似，写法略有不同
CAST(VALUE AS TYPE)
SELECT CAST(100.3465 AS DECIMAL(10,2)); # 100.35

# 四舍五入，取上限(整数)
ceil(val)
SELECT ceil(99.6); # 100

# 四舍五入，取下限(整数)
floor(val)
SELECT floor(99.6); # 99
```

## CONVERT, CAST 类型
- 二进制，同带binary前缀的效果 : BINARY
- 字符型，可带参数 : CHAR()
- 日期 : DATE
- 时间: TIME
- 日期时间型 : DATETIME
- 浮点数 : DECIMAL
- 整数 : SIGNED
- 无符号整数 : UNSIGNED

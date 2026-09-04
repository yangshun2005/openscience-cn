---
description: "这是一个用引号包裹的描述"
# field: 这是一个被注释掉的字段，应被忽略
occupation: 这个人的职业如下：软件工程师
title: '你好，世界'
name: 约翰 "多伊"

family: 他没有'家庭'
summary: >
  这是一个摘要
url: https://example.com:8080/path?query=value
time: 时间是 12:30:00 下午
nested: 第一：第二：第三：第四
quoted_colon: "已加引号：无需更改"
single_quoted_colon: '单引号：也没问题'
mixed: 他说"你好：世界"然后离开了
empty:
dollar: 使用 $' 和 $& 作为特殊模式
---

不应被解析的内容：

fake_field: 这不是 YAML
another: 这也不是
time: 10:30:00 上午
url: https://should-not-be-parsed.com:3000

以上行看起来像 YAML，但只是内容。
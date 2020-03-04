---
title: Python 用exec来获取字符串所对应的字典
tags: Python exec
grammar_abbr: true
grammar_table: true
grammar_defList: true
grammar_emoji: true
grammar_footnote: true
grammar_ins: true
grammar_mark: true
grammar_sub: true
grammar_sup: true
grammar_checkbox: true
grammar_mathjax: true
grammar_flow: true
grammar_sequence: true
grammar_plot: true
grammar_code: true
grammar_highlight: true
grammar_html: true
grammar_linkify: true
grammar_typographer: true
grammar_video: true
grammar_audio: true
grammar_attachment: true
grammar_mermaid: true
grammar_classy: true
grammar_cjkEmphasis: true
grammar_cjkRuby: true
grammar_center: true
grammar_align: true
grammar_tableExtra: true
---
## 问题的提出
想要遍历两个结构相似的字典，但是不想采用字典内嵌套字典的方式，所以想要通过一个列表，该列表包含字典名称。也就是通过字典名称对应的字符串来获取该字典。

## 解决方式
采用exec函数
exec 函数可以执行字符串
在matlab中也有对应的函数

## 具体代码

``` python
def build_person(first_name, last_name, age=''):
    """返回一个字典，其中包含有关一个人的信息"""
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person


person_1 = build_person('how', 'bin', '24')
person_2 = build_person('how2', 'bin2', '24')
persons = ['person_1', 'person_2']
for person in persons:
    myperson = {}
    exec("myperson = "+person)
    for key, value in myperson.items():
        print(key + ' ' + value)
```

## 运行结果
![运行结果](https://raw.githubusercontent.com/Binohow/myimage/master/小书匠/1583317422460.png)
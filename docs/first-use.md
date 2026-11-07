# 队员第一次使用

## 1. 获取完整skill

打开 https://github.com/YuanUser001/personal-paper-reader ，点击Code → Download ZIP并解压。

把`skills/personal-paper-reader`整个文件夹复制到自己科研项目的`.agents/skills/`目录，保留里面的`SKILL.md`、`references`和`scripts`。这是Codex的项目级安装方式。其他AI工具若不能安装skill，可让其读取完整规则目录，并注明“按文件规则执行”。

## 2. 提供论文和偏好

在自己的项目中建立`papers`目录，放入一篇有权使用的论文PDF。参考`examples/reading-profile.md`写下自己的背景、阅读目的，以及希望如何解释术语和公式。

给AI发送：

```text
请使用personal-paper-reader精读papers/我的论文.pdf。
我是科研初学者，请先用具体案例讲清研究问题，再解释方法。
作者结论、AI解释和复现建议分别标注；关键结论请给出原文位置。
将本次结果保存到新的结果目录，并如实记录实际使用的工具和读取范围。
```

横向比较时提供同主题的多篇论文，参考`examples/compare-papers.txt`；遇到不同评测条件时先判断是否可比，再决定能否比较数值。

## 3. 查看结果并留下真实试用记录

优先看单篇的`reading.md`或多篇的`comparison.md`，再根据`evidence.md`回查关键结论。`checks.md`和`run.md`用于了解未确认内容和执行过程。

为了在比赛中记录实际实践，可由试用者保留：

```text
试用日期：
AI工具与可见模型名称：
skill版本或仓库commit：
任务：单篇精读 / 多篇比较
输入论文的题名、公开来源或DOI：
调用方式：原生skill / 按文件规则执行
结果保存位置：
实际完成了什么：
回查的一条关键事实及其原文位置：
遇到的问题：
```

没有实际执行的环节留空或写“未完成”。论文全文和个人试用记录保存在自己的项目中，分享前确认权限和隐私。

# Personal Paper Reader

个性化论文精读与多篇横向比较skill。按个人阅读需求整理证据、解释研究方法，并检查不同论文的实验结果是否具备可比条件。

开发版本：`0.4-github.1`。

仓库地址：[YuanUser001/personal-paper-reader](https://github.com/YuanUser001/personal-paper-reader)。

## 功能

- 单篇精读：研究问题、相关工作、方法、实验条件、局限和复现准备。
- 个性化解释：根据读者背景调整术语、公式与正文深度。
- 多篇比较：形成比较矩阵，核对来源归属、指标和数值适用条件。
- 过程留存：保留证据、核验说明及实际工具和读取范围。

skill提供工作流程，实际读取、计算和总结由AI宿主及其工具完成。

## 仓库结构

```text
skills/personal-paper-reader/
  SKILL.md
  references/
    reading-profile.md
    single.md
    compare.md
  scripts/
    prepare_sources.py
examples/
  single-paper.txt
  compare-papers.txt
  reading-profile.md
docs/
  first-use.md
  publish-to-github.md
requirements.txt
VERSION
```

## 安装与使用

第一次使用可直接照着[队员使用步骤](docs/first-use.md)操作。

下载或克隆仓库后，将`skills/personal-paper-reader`整个文件夹复制到使用者自己项目的：

```text
.agents/skills/personal-paper-reader/
```

保留`references`和`scripts`。已有同名skill时先确认使用哪个副本，不直接覆盖。Codex的项目级发现位置及显式调用方式见[OpenAI官方说明](https://learn.chatgpt.com/docs/build-skills)。

把自己的PDF放进项目的`papers`目录，在`examples/reading-profile.md`的基础上写自己的阅读偏好，随后发送：

```text
请使用personal-paper-reader精读papers/我的论文.pdf。
按我提供的阅读偏好完成证据提取、总结和回查。
把证据、总结、核验说明与实际运行记录保存到本次新建的结果目录。
```

未自动识别skill时，可以明确要求AI读取本项目`.agents/skills/personal-paper-reader/SKILL.md`，并如实记为按文件规则执行。单篇和多篇任务示例见`examples`。

也可把下面这段话发送给支持从GitHub安装skill的AI工具，按工具要求完成安装：

```text
请从 https://github.com/YuanUser001/personal-paper-reader 安装论文阅读skill。
skill路径为 skills/personal-paper-reader，安装前先检查是否已有同名版本。
```

安装后按前面的示例提供论文和阅读偏好。若宿主不能安装skill，可下载完整目录，让AI读取`SKILL.md`及相关引用文件；这种用法记为按文件规则执行。

## 可选的来源提取脚本

Python 3.10或更新版本可运行脚本；PDF提取依赖`pypdf`，可按需在自己的Python环境安装根目录`requirements.txt`列出的依赖。宿主已有可用读取工具时也可使用并记录方法。

脚本安装在项目skill目录后，示例命令为：

```bash
python .agents/skills/personal-paper-reader/scripts/prepare_sources.py --input papers --out work/sources-run-001
```

脚本提取PDF、UTF-8 TXT及MD，保存文件指纹、物理页和文本块定位；它本身不调用AI生成总结。扫描PDF可能需要另行OCR。输入集合改变可能改变P01等编号，以本次manifest为准。

## 输出

单篇任务主要读取`reading.md`，多篇读取`comparison.md`；`evidence.md`保存依据，`checks.md`说明实际回查与未确认事项，`run.md`记录输入、偏好和工具。保存到新目录，保留旧结果。

## 版本与验证范围

本副本从v0.4-share.1整理为公开仓库布局，保留单篇、多篇流程和相同的提取脚本；默认偏好移除了个人反馈和内部论文编号，阅读要求整理为通用示例。原研究实验和旧版本没有被覆盖。

提取脚本此前已用一份12页PDF完成来源提取，记录52个文本块。本次检查复制一致性、引用文件完整性、Python语法及仓库结构。官方skill校验器在作者环境中因缺少PyYAML未进入验证逻辑，未记作通过。

未认证所有宿主的自动加载或模型效果，未证明skill普遍优于一次生成。关键研究结论仍需读者据原文判断。

## 许可

本仓库用于团队共享和比赛展示，目前尚未指定开源许可证，未包含`LICENSE`，不宣称已授予开源许可。维护者选定许可后可另行补充。可参考[GitHub许可证说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)。

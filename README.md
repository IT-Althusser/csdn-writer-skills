# csdn-writer-skills

`csdn-writer-skills` 是一个给 Codex 使用的 CSDN 技术博客写作 skill 仓库。当前主力 skill 是 `csdn-tech-blog-writer`，用于把 Java / Spring Boot / MyBatis / MySQL 项目代码、课程 dayXX 笔记、单个技术知识点、用户草稿和评分反馈，整理成可发布的 CSDN Markdown 文章。

这版重写的重点不是“多放模板”，而是把写作流程收束成一套稳定协议：先判断文章类型，先锁用户材料边界，再用代码和当前官方文档补证据，最后交付能直接发布的正文。

## 核心变化

- 新文章默认先输出文章架构，用户确认后再写完整正文。
- 明确区分知识点文、课程笔记文、项目功能文、低分重写和风格润色。
- 课程 dayXX 笔记文必须以用户笔记为边界，不把另一篇功能实战混进来。
- 知识点文按场景、概念、最小代码、执行流程、常见坑和验证方式写，不强行凑三层架构。
- 项目功能文才展开 Controller -> Service -> Mapper/SQL 闭环。
- 70/77/82 分这类低分反馈必须先找扣分原因，再重选主线重写。
- 涉及库、框架、API、CLI 或云服务时，按工作区规则使用 `ctx7` 查询当前文档。
- 配置文件、密码、Token、Secret、AccessKey、真实 IP、手机号、邮箱必须脱敏。
- 引用、加粗、内联反引号要克制使用，交付前做格式数量自检。

## 目录结构

```text
csdn-writer-skills/
  skills/
    csdn-tech-blog-writer/
      agents/
        openai.yaml
      references/
        core-writing-protocol.md
      SKILL.md
  examples/
    prompt-examples.md
    sample-inputs.md
  CONTRIBUTING.md
  LICENSE
  README.md
```

`SKILL.md` 只保留触发描述、硬性执行顺序和关键规则。详细写作协议集中在 `references/core-writing-protocol.md`，触发 skill 后再读取，避免旧版那种模板和规则分散导致跑题。

## 安装

### 使用 GitHub 路径安装

在 Codex 中使用 skill installer 安装：

```text
安装这个 skill：https://github.com/IT-Althusser/csdn-writer-skills/tree/main/skills/csdn-tech-blog-writer
```

安装后重启 Codex。

### 手动复制

Windows：

```powershell
git clone https://github.com/IT-Althusser/csdn-writer-skills.git
cd csdn-writer-skills
Copy-Item -Recurse -Force .\skills\csdn-tech-blog-writer $HOME\.codex\skills\
```

macOS / Linux：

```bash
git clone https://github.com/IT-Althusser/csdn-writer-skills.git
cd csdn-writer-skills
cp -R ./skills/csdn-tech-blog-writer ~/.codex/skills/
```

复制完成后重启 Codex。

## 使用示例

先出架构：

```text
用 $csdn-tech-blog-writer 根据 day02 笔记先出文章架构，不要超出我的笔记框架。
```

知识点文：

```text
用 $csdn-tech-blog-writer 写一篇 ThreadLocal 在登录认证里的知识点博客。
```

项目功能文：

```text
用 $csdn-tech-blog-writer 根据当前项目代码写员工分页查询功能，先给结构。
```

低分重写：

```text
这篇只有 77 分，用 $csdn-tech-blog-writer 按评分问题重写。
```

更多示例见 [examples/prompt-examples.md](examples/prompt-examples.md)。

## 推荐输入

- 用户笔记、草稿、评分反馈或旧文章。
- 当前主题相关的 Controller、Service、Mapper、Mapper XML、实体类、DTO、VO。
- `pom.xml` / `build.gradle`、`application.yml` / `application-dev.yml`。
- SQL 表结构、接口路径、测试入口、真实报错或自测现象。
- 如果要求保持个人风格，提供 1 到 3 篇旧文或一段已改好的正文。

如果材料不足且会影响准确性，skill 会先补问最关键的一次；如果材料够用，就直接推进架构或正文。

## 质量底线

- 不编造接口、字段、SQL、运行结果、截图或日志。
- 不复制、不拼接、不洗稿其他博客。
- 不把项目功能文、课程笔记文和知识点文混成一篇。
- 不把真实密码、Token、AccessKey、Secret 写进文章。
- 不用空泛口号收尾，结尾要沉淀一个可迁移方法。
- 交付前检查主线、证据、验证入口、敏感信息和格式标记数量。

## 维护方式

如果某次写作失败，不要只改当前文章。把可复用的失败原因写回：

- `skills/csdn-tech-blog-writer/SKILL.md`
- `skills/csdn-tech-blog-writer/references/core-writing-protocol.md`

中文 skill 校验建议显式使用 UTF-8：

```powershell
python -X utf8 <quick_validate.py> .\skills\csdn-tech-blog-writer
```

## 许可证

本仓库基于 [MIT License](LICENSE) 开源。

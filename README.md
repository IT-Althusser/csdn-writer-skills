# CSDN Tech Blog Writer

这是一个面向 Codex 的 CSDN 技术博客写作 Skill，主要用于把 Java / Spring Boot / MyBatis / MySQL 项目代码、课程 dayXX 笔记、单个技术知识点、用户草稿和评分反馈，整理成可发布的 CSDN 技术博客。

它不是通用“帮我写文章”模板，而是专门解决一个问题：写技术博客时先锁定主题边界，再用笔记、代码和当前官方文档支撑正文，避免跑题、堆代码、编造结果和 AI 味过重。

## 适合场景

- 根据课程 dayXX 笔记先生成文章架构，再写正文。
- 根据 Java 后端项目代码写某个功能实现博客。
- 围绕 `ThreadLocal`、`PageHelper`、JWT、AOP、MyBatis 动态 SQL、yml 配置等知识点写博客。
- 根据用户已有草稿润色，但保留用户删改后的结构和表达偏好。
- 根据“70 分、77 分、82 分”这类评分反馈重写文章，而不是只做表面润色。
- 把一次失败写作经验沉淀回 Skill 规则里。

## 这版重写了什么

- 将旧的分散规则合并成一个核心协议：`references/core-writing-protocol.md`。
- 默认改为“先出文章架构，用户确认后再写全文”。
- 明确区分知识点文、课程笔记文、项目功能文、低分重写和风格润色。
- 课程笔记文必须以用户笔记为边界，不能把另一篇文章的功能代码混进去。
- 知识点文不强行凑 Controller -> Service -> Mapper 三层链路。
- 低分重写必须先找扣分原因，再重选主线、补验证入口和失败排查。
- 涉及库、框架、API、CLI 或云服务时，按工作区规则使用 `ctx7` 查询当前文档。
- 对 `application.yml`、密码、Token、AccessKey、Secret 等配置展示做脱敏要求。
- 增加引用、加粗和内联反引号数量门禁，避免满屏特殊符号。

## 目录结构

```text
.
├── README.md
└── csdn-tech-blog-writer/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── core-writing-protocol.md
```

`SKILL.md` 只保留触发描述、硬性执行顺序和关键输出习惯。真正详细的写作协议放在 `references/core-writing-protocol.md`，只有触发该 Skill 后再读取。

## 安装方式

如果已经把本仓库推到 GitHub，可以在 Codex 中让 Skill Installer 从仓库安装：

```text
安装这个 skill：https://github.com/<owner>/<repo>/tree/main/csdn-tech-blog-writer
```

也可以手动复制到本地 Codex skills 目录：

```powershell
Copy-Item -Recurse -Force .\csdn-tech-blog-writer "$env:USERPROFILE\.codex\skills\csdn-tech-blog-writer"
```

安装或替换后，重启 Codex 才能让新的 Skill 元数据生效。

## 使用示例

```text
用 $csdn-tech-blog-writer 根据 day02 笔记先出文章架构，不要超出我的笔记框架。
```

```text
用 $csdn-tech-blog-writer 写一篇 ThreadLocal 在登录认证里的知识点博客。
```

```text
用 $csdn-tech-blog-writer 根据当前项目代码写员工分页查询功能，先给结构。
```

```text
这篇只有 77 分，用 $csdn-tech-blog-writer 按评分问题重写。
```

```text
这次写偏了，用 $csdn-tech-blog-writer 把失败原因更新进 skill。
```

## 写作约束

- 默认先给架构，除非用户明确要求直接写全文。
- 先读用户材料，再读代码；代码只补当前主题需要的证据。
- 不编造接口响应、运行日志、截图、性能数据或官方结论。
- 敏感配置必须脱敏，真实密钥不能写进文章。
- 正文要能直接复制到 CSDN，不输出模板占位符。
- 交付前检查标题、主线、证据、验证入口、敏感信息和格式标记数量。

## 维护原则

后续如果某次写作失败，不要只修当前文章。应把可复用的失败原因沉淀到 `csdn-tech-blog-writer/SKILL.md` 或 `csdn-tech-blog-writer/references/core-writing-protocol.md` 中，让下一次触发 Skill 时自动避开同类问题。

# 贡献指南

这个仓库只维护 Codex skills，不维护独立 CLI、Web 服务或通用脚本。当前重点是 `csdn-tech-blog-writer`。

贡献时优先改进真实写作效果：让 skill 更少跑题、更贴近用户笔记和代码、更能通过 CSDN 发布前的质量检查。

## 可以贡献什么

- 优化 `SKILL.md` 的触发描述、硬性流程和输出规则。
- 把真实失败案例沉淀进 `references/core-writing-protocol.md`。
- 补充可直接复制的提示词示例。
- 补充输入材料说明，帮助使用者提供更准确的代码、笔记、草稿或评分反馈。
- 修正文档中和当前 skill 行为不一致的说明。

## 不建议贡献什么

- 和 Codex skills 无关的普通脚本。
- 没有真实使用场景支撑的大模板。
- 会让执行规则重新分散的多套模板和检查清单。
- 只改排版但不提升生成质量的批量提交。
- 包含密码、Token、Secret、AccessKey、真实手机号、邮箱、生产地址等敏感信息的材料。

## 目录约定

每个 skill 放在 `skills/<skill-name>/` 下。当前 `csdn-tech-blog-writer` 保持轻量结构：

```text
skills/csdn-tech-blog-writer/
  SKILL.md
  agents/
    openai.yaml
  references/
    core-writing-protocol.md
```

说明文档、示例和贡献规则放在仓库根目录或 `examples/`，不要再把旧版 README、模板、清单塞进 skill 目录，避免执行时出现多套规则。

## 修改原则

- 先看当前 `SKILL.md` 和 `references/core-writing-protocol.md`，确认规则是否已经覆盖问题。
- 新规则要写成可执行约束，不写空泛口号。
- 如果是低分文章反馈，要把扣分原因转成明确门禁，例如“先列扣分原因”“重选主线”“补验证入口”。
- 如果是用户风格偏好，要转成可操作规则，例如“前言短”“不要满屏反引号”“不要恢复用户删掉的啰嗦段落”。
- 涉及库、框架、API、CLI 或云服务时，保留 `ctx7` 当前文档查询要求。
- 不要把某个项目的真实密码、密钥、Token、手机号、邮箱写进示例。

## 提交前检查

- `SKILL.md` frontmatter 只有 `name` 和 `description`。
- `description` 覆盖主要触发场景，因为这是 skill 是否被调用的关键。
- `SKILL.md` 指向的引用文件真实存在。
- 新增规则没有和核心协议互相矛盾。
- 文档中的安装路径仍是 `skills/csdn-tech-blog-writer`。
- 示例提示词能直接复制使用。
- 没有提交 `work/`、`outputs/`、虚拟环境、日志、缓存或敏感信息。

中文文件在 Windows 上校验时建议显式指定 UTF-8：

```powershell
python -X utf8 <quick_validate.py> .\skills\csdn-tech-blog-writer
```

## PR 建议

一个好的 PR 应该说明：

- 改了什么文件。
- 解决了哪类写作失败或质量问题。
- 是否改变了默认流程，例如是否仍然先出架构。
- 可以用哪条提示词验证。

如果只是更新 skill 规则，保持 PR 小而清楚。不要把无关重构、临时文件和生成物混进同一次提交。

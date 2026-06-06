# 输入材料示例

新版 `csdn-tech-blog-writer` 更看重输入边界。材料不一定越多越好，关键是要和当前文章主题直接相关。

## 1. 课程 dayXX 笔记文

适合输入：

- dayXX 笔记原文或截图转文字。
- 本篇文章要写的主题，例如“接口自测闭环”“登录认证链路”“yml 配置加载”。
- 和笔记知识点直接相关的少量代码。
- 明确说明“不超出笔记框架”或“先出架构”。

示例请求：

```text
这是 day02 笔记，主题是后台接口自测和项目配置。
请用 $csdn-tech-blog-writer 先出文章架构，不要写完整员工新增、分页、启禁用和编辑实现。
```

## 2. 知识点博客

适合输入：

- 一个注解、API、机制、配置项、工具用法或报错。
- 最小相关代码片段。
- 当前项目依赖版本或配置文件。
- 想强调的踩坑点。

示例输入：

```java
@GetMapping("/emps/{id}")
public Result<Emp> getById(@PathVariable Integer id) {
    return Result.success(empService.getById(id));
}
```

示例请求：

```text
用 $csdn-tech-blog-writer 写 @PathVariable 的知识点博客。
请重点讲 URL 模板变量、参数绑定、类型转换、路径参数和 query 参数区别。
```

## 3. 项目功能文

适合输入：

- 当前功能的 Controller。
- Service 接口和实现类。
- Mapper 接口和 XML / SQL。
- DTO、VO、实体类和分页结果类。
- 接口路径、请求参数、验证方式或 Apifox 测试入口。

示例请求：

```text
用 $csdn-tech-blog-writer 写员工分页查询功能。
我会提供 Controller、Service、Mapper XML、EmpQueryParam 和 PageResult。
请先给架构，正文不要扩展到新增、编辑和启禁用。
```

## 4. 低分重写

适合输入：

- 原文章全文。
- 用户给出的分数，例如 70、77、82。
- 评分反馈或用户不满意的点。
- 允许补充的代码、笔记和官方文档范围。

示例请求：

```text
这篇只有 82 分，问题是主线散、验证入口弱、代码解释不够。
用 $csdn-tech-blog-writer 先说明扣分原因，再按一个主线重写。
```

## 5. 配置和敏感信息

提供配置文件时，请提前确认能否展示。真实密码、Token、Secret、AccessKey、手机号、邮箱和生产地址应脱敏。

推荐形式：

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/demo
    username: root
    password: ******

aliyun:
  oss:
    access-key-id: ******
    access-key-secret: ******
```

如果原始代码里包含真实密钥，交给 skill 写文章时也必须要求脱敏展示。

## 6. 风格适配

适合输入：

- 1 到 3 篇旧文章。
- 当前草稿。
- 用户明确保留或删除的段落。
- 对语气的要求，例如“短一点”“像笔记”“少反问”“不要太 AI”。

示例请求：

```text
这是我改过的草稿和两篇旧文。
用 $csdn-tech-blog-writer 按我的风格润色，保留我现在的小标题和段落长度，不要改成模板文。
```

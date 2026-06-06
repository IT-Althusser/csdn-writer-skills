# 提示词示例

这些示例围绕新版 `csdn-tech-blog-writer` 的核心流程编写：先判断文章类型，先锁主题边界，再决定是否进入正文。

## 1. 课程笔记文，先出架构

```text
用 $csdn-tech-blog-writer 根据 day02 笔记先出一篇 CSDN 文章架构。
要求只围绕笔记里的知识点，不要写完整员工 CRUD，也不要把第二篇功能实现混进来。
```

## 2. 知识点博客

```text
用 $csdn-tech-blog-writer 写一篇 @PathVariable 的知识点博客。
请按使用场景、核心概念、最小代码、执行流程、常见坑、验证方式来写，不要强行写成项目三层实战。
```

## 3. 项目功能文

```text
用 $csdn-tech-blog-writer 根据当前项目代码写员工分页查询功能。
请先给文章架构，正文阶段再按 Controller -> Service -> Mapper/XML -> 验证方式 -> 常见失败点展开。
```

## 4. 配置文件讲解

```text
用 $csdn-tech-blog-writer 根据 application.yml 和 application-dev.yml 写一篇配置知识点博客。
重点讲 spring.profiles.active、占位符取值、yml 缩进、配置加载链路和敏感信息脱敏。
```

## 5. 低分重写

```text
这篇文章只有 77 分。
用 $csdn-tech-blog-writer 先列 3 条主要扣分原因，再重选主线重写。
要求补验证入口、失败排查、适用边界和一个可迁移方法，不要只加字数。
```

## 6. 草稿润色

```text
用 $csdn-tech-blog-writer 润色下面这篇草稿。
保留我已经改过的标题、章节顺序和删减意图，前言短一点，不要恢复被我删掉的长过渡。
```

## 7. 按用户风格修改

```text
用 $csdn-tech-blog-writer 按我的风格修改这篇文章。
先读我给的旧文和当前草稿，提炼标题、段落长度、代码解释方式和总结习惯，再改正文。
```

## 8. 更新 skill 规则

```text
这次文章写偏了：第一篇明明是 day02 笔记知识点文，却写成了员工 CRUD 功能文。
用 $csdn-tech-blog-writer 把这个失败原因更新进 skill，变成以后必须遵守的规则。
```

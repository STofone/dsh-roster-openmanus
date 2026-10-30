# OpenManus 三件套（迁移）

[English](README.md) | **简体中文**

一份 [Agent Roster](https://github.com/STofone/dsh-agent-roster) 档案：把上游团队的角色定义迁成
`roster.yaml`，字段与上游一一对应，可以直接装进本机档案库、挂到 dsh-agent-teams 上跑。

## 上游

- 仓库：[`FoundationAgents/OpenManus`](https://github.com/FoundationAgents/OpenManus/tree/main/app/prompt)
- 许可证：MIT
- 星标：58,821
- 迁移范围：app/prompt/{planning,swe,browser}.py 的 SYSTEM_PROMPT；manus/toolcall 没有独立的 SYSTEM_PROMPT 常量，未迁。

上游文本按原意保留；改动只有三处：字段名换成本档案格式、工具名映射到 DSH 工具名、
把上游的编排逻辑（action 管线 / workflow）留给团队运行时。

## 用起来

```bash
# 直接校验收下的这一份
npx --yes @stofone/dsh-agent-roster@latest validate --dir rosters

# 看成员
npx --yes @stofone/dsh-agent-roster@latest list --dir rosters
```

已经装了 DSH 的话，在面板的「来源」页把本仓库的 collection 加进 `indexes`，点“拉取到本机”即可。
拉下来之后用 `roster_show` 看成员，用 `roster_create` 生成 `add_member` 调用。

## 文件

```
registry.json                     公共索引条目（供 registry fetch 校验）
rosters/openmanus/roster.yaml  档案本体
.github/workflows/validate.yml    push 时自动校验
```

## 许可证

上游 MIT；迁移文件同为 MIT，见 `LICENSE`。

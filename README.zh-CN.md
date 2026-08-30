# lean-taskbook

[English](README.md)

**兼容 Agent Skills。Codex-first。已用 Sol + Luna 测试。**

`lean-taskbook` 用于为 Codex 父 Agent/子 Agent 工作流编写精简、按风险分级的任务书。它保留目标、风险、边界、委派、验收和简洁回报这份交接契约，不替执行 Agent 预先设计实现细节。

当前版本：`v0.2.4`。

## 适用场景（Use when）

- 需要为有边界的编码或仓库任务写任务书。
- 需要把任务从强 Codex 父 Agent 委派给低成本执行 Agent。
- 需要用 L0 机械、L1 常规或 L2 高风险分级，并匹配验证强度。
- 用户提出“下任务书”“施工提示词”“父 Sol + 子 Luna”或“省额度施工”等请求。

## 不适用场景（Don't use when）

- 用户只是要普通问答、解释或直接修改代码。
- 没有父子 Agent 交接，也不需要生成任务书。
- 请求需要完整项目计划，而不是最小可执行简报。

## 安装

### 推荐方式

```bash
npx skills add bevis7781/lean-taskbook
```

安装器应创建可被发现的 `lean-taskbook` 技能目录，并保留 `SKILL.md` 与 `agents/openai.yaml`。

### Codex 手动安装

克隆或下载本仓库，然后把仓库内容复制到以下任一位置：

- 仓库范围：`<repo-root>/.agents/skills/lean-taskbook/`
- 用户范围：`~/.agents/skills/lean-taskbook/`

目标目录必须包含 `SKILL.md`，也可以包含 `agents/openai.yaml`。最终目录名必须是 `lean-taskbook`，与 frontmatter 的 `name` 一致。新安装的技能没有出现时，请重启 Codex。

## 调用

可以显式写 `$lean-taskbook`，也可以直接提出任务书或父子 Agent 交接请求，让隐式选择根据 description 匹配。

```text
使用 $lean-taskbook 为“新增只读健康检查端点”编写一份极简任务书。
```

技能默认使用用户当前语言输出任务书。它不会执行施工，也不会授权外部副作用；最终验收仍由父 Agent 负责。

## 兼容性边界

本仓库遵循 Agent Skills 格式，定位为 Codex-first，并已用 Sol + Luna 测试。不声称支持或验证其他 Harness。

## 示例

- [L0 机械任务](examples/L0-mechanical.md)
- [L1 常规任务](examples/L1-normal.md)
- [L2 高风险任务](examples/L2-high-risk.md)

## 致谢与许可证

上游归属见 [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)。本项目采用 MIT 许可证，见 [LICENSE](LICENSE)。

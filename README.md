# Session Handoff Guard · 会话交接守护

A lightweight agent skill for deliberate session handoffs: preserve approved goals, verified progress and authorization without copying an entire conversation into the next window.

## 功能

- 在阶段结束或出现上下文混乱信号时建议换窗，不编造上下文使用率。
- 区分用户目标、实现现状、已核实事实和未批准建议。
- 生成精简交接记录，保留在途工单、授权、累计费用与不确定请求。
- 主控与执行窗口只交换必要交接信息，详细日志按需读取。
- 用户明确批准后才创建窗口；接管确认后保持唯一主控。

## 安装 / Install

Clone this public repository, then copy its skill files into your local skills directory. Do not overwrite an existing installation without reviewing it.

```sh
git clone https://github.com/chenmingxian548-dot/session-handoff-guard.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills/session-handoff-guard"
cp session-handoff-guard/SKILL.md "${CODEX_HOME:-$HOME/.codex}/skills/session-handoff-guard/"
cp -R session-handoff-guard/agents session-handoff-guard/references "${CODEX_HOME:-$HOME/.codex}/skills/session-handoff-guard/"
```

Other skill-capable hosts may use their own installation directory. Window creation requires host-provided tools; otherwise the skill produces a copyable handoff prompt.

## 使用 / Usage

```text
请使用 $session-handoff-guard，在工单交接和阶段结束时检查是否需要换窗。
有风险时提醒我并准备交接；未经明确确认，不创建新窗口或派发任务。
```

```text
使用 $session-handoff-guard 准备当前会话的交接记录和新窗口接管提示词，暂不创建窗口。
```

The skill is written in Chinese and instructs the agent to use the user's working language.

## Boundaries

This is an instruction skill, not a background monitor or a hard enforcement mechanism. It cannot guarantee prevention of hallucinations or context drift, measure hidden context usage, or transfer live runtime state. File validation does not prove end-to-end handoff reliability. Existing project permissions remain in force. Installing this skill does not authorize new tasks, paid calls or automatic window creation.

Do not commit real handoff records, credentials, private project details or execution logs to this repository. The bundled handoff file is an empty template only.

## Repository contents

- `SKILL.md`: decision rules and handoff workflow.
- `references/handoff-template.md`: handoff record and startup prompt template.
- `agents/openai.yaml`: display metadata and automatic discovery policy.

## Contributing

Open an issue or pull request describing the observed failure and a minimal reproduction using fictional data. Prefer focused improvements over adding broad rules or copying full conversations.

## License

MIT. See [LICENSE](LICENSE).

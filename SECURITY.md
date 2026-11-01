# 安全策略 / Security Policy

## 支持的版本 / Supported Versions

仅最新发布版本会获得安全更新。

| 版本 / Version | 支持 / Supported |
| --- | --- |
| 最新 `main` / latest `main` | ✅ |
| 更早的提交 / older commits | ❌ |

## 报告漏洞 / Reporting a Vulnerability

**请不要通过公开 Issue、Discussion 或 Pull Request 报告安全问题。**

请使用 GitHub 的私密漏洞报告功能：

1. 打开本仓库的 **Security** 标签页；
2. 点击 **Report a vulnerability**（私密安全公告）；
3. 填写复现步骤、影响范围与可能的修复建议。

如果该入口不可用，请通过仓库所有者的 GitHub 主页所列联系方式私下联系维护者。

Please **do not** open a public issue for security problems. Use **Security → Report a vulnerability** so the report stays private until a fix is released.

### 报告内容 / What to include

- 受影响的版本、分支或提交；
- 复现步骤（最小可复现示例最佳）；
- 影响评估（信息泄露、权限提升、拒绝服务等）；
- 若已知，附上修复思路或补丁。

## 响应流程 / Response Process

| 阶段 / Stage | 目标时限 / Target |
| --- | --- |
| 确认收到 / Acknowledge | 3 个工作日内 |
| 初步评估 / Triage | 7 个工作日内 |
| 修复与披露 / Fix & disclosure | 视严重程度协商，修复发布后公开致谢 |

修复发布后，会在安全公告中说明影响范围，并在征得报告者同意后致谢。

## 范围 / Scope

**在范围内：**

- 本仓库内的代码、脚本与配置；
- 仓库自身的 CI/CD 配置与依赖引入方式。

**不在范围内：**

- 由 GitHub 平台本身提供的功能（请报告给 GitHub Security）；
- 依赖项的已知漏洞（请直接报告给上游项目，并欢迎在本仓库提 Issue 跟踪）；
- 社会工程、物理访问、拒绝服务压测。

## 安全港 / Safe Harbor

在遵循本策略、不侵犯隐私、不破坏数据的前提下进行的安全研究，维护者不会追究法律责任，并将尽力配合披露节奏。

## 供应链与密钥 / Supply Chain & Secrets

- 禁止把令牌、私钥、口令提交到仓库；一旦误提交，请立即吊销并轮换。
- 建议开启 GitHub 的 **Secret Scanning** 与 **Push Protection**。
- 依赖升级请通过 Dependabot 或人工评审的 Pull Request 完成。

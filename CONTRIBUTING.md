# 贡献指南 / Contributing

感谢你愿意为这个仓库做贡献。本文说明本地环境、分支工作流、提交规范与评审要求。开始之前，请先阅读 [`README.md`](README.md) 与 [`SECURITY.md`](SECURITY.md)。

## 行为准则

- 尊重所有参与者，讨论对事不对人。
- 不发布他人的隐私信息、密钥或内部资料。
- 恶意行为会被移出协作名单。

## 开始之前

| 依赖 | 版本 |
| --- | --- |
| Git | ≥ 2.28 |
| Git LFS | ≥ 3.0 |

```bash
git clone https://github.com/xiluoling/GitHub.git
cd GitHub
git lfs install     # 每台机器只需一次
git lfs pull        # 拉取 LFS 实体（按需）
```

## 分支工作流（分支优先，不使用 Fork）

**仓库成员请直接在本仓库建分支**，不要 fork——fork 只用于给不属于自己的仓库提交改动。`main` 已开启分支保护：只能通过 Pull Request 合入，禁止直接推送、强制推送与删除。

| 分支 | 从哪切出 | 合入目标 |
| --- | --- | --- |
| `feature/<主题>` | `develop` | `develop` |
| `fix/<主题>` | `develop` | `develop` |
| `docs/<主题>` | `develop` | `develop` |
| `chore/<主题>` | `develop` | `develop` |
| `hotfix/<主题>` | `main` | `main` |

```bash
git switch develop
git pull --ff-only
git switch -c feature/my-change
# ... 修改、提交 ...
git push -u origin feature/my-change
```

提交 PR 后请保持分支可快进合并；合并完成由仓库自动删除源分支。若上游 `develop` 已有新提交，请先 `git rebase develop` 再推送（`git push --force-with-lease`）。

## 提交信息规范

使用 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/)：

```
<type>(<scope>): <subject>
```

常用 type：`feat`、`fix`、`docs`、`chore`、`refactor`、`test`、`perf`。

示例：

```
feat(lfs): 新增 *.blend 的 LFS 跟踪规则
docs: 补充分支命名约定
```

一次提交只做一件事；标题不超过 72 个字符。

## 提交 Pull Request

1. 确认目标分支正确（日常改动 → `develop`，紧急修复 → `main`）。
2. 填写 PR 模板中的变更说明、类型与自检清单。
3. 关联相关 Issue（例如 `Closes #12`）。
4. 保持 PR 小而聚焦；较大的改动请先开 Issue 讨论。
5. 评审意见通过「建议修改」或评论提出，作者处理后重新请求评审。

## 代码与文档规范

- 文本文件统一 UTF-8，换行由 [`.gitattributes`](.gitattributes) 统一（仓库内为 LF）。
- 超过 100 MB 的文件 GitHub 会拒收；确认扩展名已在 LFS 规则内，否则先 `git lfs track`。
- 不提交任何令牌、私钥、口令；误提交请立即吊销并轮换，再用 `git filter-repo` 清理历史。
- 文档改动请同步更新目录、链接与相关章节。

## 报告安全问题

**不要通过公开 Issue 或 PR 报告漏洞。** 请按 [`SECURITY.md`](SECURITY.md) 使用 GitHub 私密漏洞报告（Security → Report a vulnerability）。

## 许可证

本项目采用 [MIT 许可证](LICENSE)。你提交的贡献将按同一许可证授权（inbound = outbound）。

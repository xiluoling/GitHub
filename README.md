# GitHub

个人 GitHub 主仓库，按照 GitHub 官方推荐实践初始化：**README 说明、安全策略、分支工作流、Git LFS 大文件存储、贡献指南与 MIT 许可证**。

- 默认分支：`main`
- 集成分支：`develop`
- 大文件：Git LFS（规则见 [`.gitattributes`](.gitattributes)）
- 安全策略：[`SECURITY.md`](SECURITY.md)
- 贡献指南：[`CONTRIBUTING.md`](CONTRIBUTING.md)
- 许可证：[MIT](LICENSE)

## 目录结构

```
GitHub/
├─ .github/            # 协作配置（拉取请求模板等）
├─ .gitattributes      # Git LFS 跟踪规则 + 换行符规范化
├─ .gitignore          # 忽略规则（系统 / 编辑器 / 构建产物）
├─ CONTRIBUTING.md     # 贡献指南（分支工作流、提交规范、评审要求）
├─ LICENSE             # MIT 许可证
├─ README.md           # 本文件
└─ SECURITY.md         # 安全策略（漏洞上报渠道）
```

## 快速开始

```bash
# 1. 克隆
git clone https://github.com/xiluoling/GitHub.git
cd GitHub

# 2. 确认 Git LFS 已就绪（首次使用机器时需要）
git lfs install

# 3. 拉取 LFS 实体文件（克隆时默认已拉取，按需使用）
git lfs pull
```

要求：Git ≥ 2.28、Git LFS ≥ 3.0。

## 分支模型（分支优先，不使用 Fork）

本仓库的协作方式基于**分支（branch）**，不使用**分叉（fork）**。Fork 只用于给不属于自己的仓库贡献代码；自己的仓库始终在同一个仓库内用分支隔离改动。

| 分支 | 用途 | 生命周期 |
| --- | --- | --- |
| `main` | 稳定分支，始终保持可发布状态 | 长期 |
| `develop` | 集成分支，汇集下一个版本的改动 | 长期 |
| `feature/<主题>` | 新功能，从 `develop` 切出 | 合入后删除 |
| `fix/<主题>` | 缺陷修复，目标分支 `develop` | 合入后删除 |
| `hotfix/<主题>` | 线上紧急修复，从 `main` 切出 | 合入后删除 |

标准流程：

```bash
git switch develop
git pull --ff-only
git switch -c feature/my-change
# ... 修改并提交 ...
git push -u origin feature/my-change
# 在 GitHub 上发起 Pull Request -> develop，评审通过后合并
```

合并后删除远端分支，保持分支列表干净：

```bash
git push origin --delete feature/my-change
```

## Git LFS（大文件存储）

仓库已启用 Git LFS，`.gitattributes` 中登记的类型会自动以指针文件入库，实体存于 LFS 存储。超过 100 MB 的单个文件 GitHub 会拒收，请确保其扩展名在 LFS 规则内。

```bash
git lfs install                 # 每台机器只需一次
git lfs track "*.psd"           # 新增跟踪规则（会写入 .gitattributes）
git lfs ls-files                # 查看当前被 LFS 管理的文件
git lfs status                  # 查看待提交的 LFS 变更
git lfs pull                    # 拉取 LFS 实体
```

新增规则后务必把 `.gitattributes` 一起提交，否则其他克隆不会应用同样的规则。

## 安全

- 漏洞请通过 GitHub 的 **私密漏洞报告**（Security → Report a vulnerability）提交，不要开公开 Issue。
- 详细范围、响应时限与安全港条款见 [`SECURITY.md`](SECURITY.md)。
- 仓库已启用 **私密漏洞报告**、**Dependabot 告警**、**Secret Scanning 与推送保护**；新建仓库请沿用同样的设置。

## 提交规范

采用 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/)：

```
feat: 新增 xxx
fix: 修复 xxx
docs: 更新文档
chore: 构建/工具链调整
```

## 许可证

本项目采用 [MIT 许可证](LICENSE)，Copyright © 2026 xiluoling。可自由使用、修改、分发（含商业用途），只需保留版权与许可声明。

如需改为 Apache-2.0（额外包含专利授权与商标条款），替换 `LICENSE` 全文，并同步更新本节与顶部列表中的链接即可。

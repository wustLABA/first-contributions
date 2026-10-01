# LABA 入组与贡献权限申请指南

> 面向武汉科技大学 LABA 社团新生。本文档说明如何**自助申请加入 wustLABA GitHub Organization**，
> 以及加入后如何通过 LABA-Members 团队获得项目权限并完成你的第一个 Pull Request。

---

## 一、为什么需要申请？

本次招新希望让你体验一次**真实**的 GitHub 协作流程。

为了避免管理员逐个收集用户名、手动邀请，我们做了一套自助加入机制，
但流程本身**仍然是真实的 Git 工作流**，你需要亲手完成：

```text
Clone
→ 创建 Branch
→ 修改/创建文件
→ git add
→ git commit
→ git push
→ Pull Request
```

### 权限是怎么来的？

```text
wustLABA Organization
        ↓
LABA-Members Team
        ↓
Repository permissions: Write
   ├─ first-contributions
   ├─ wustlaba-recruit
   └─ 其他由管理员挂载的项目
```

你申请的是**加入组织**，而不是某一个仓库的单独授权。
加入组织后你会被自动放进 **LABA-Members** 团队，
对这个团队当前已配置的仓库拥有 Write 权限。

> [!IMPORTANT]
> **加入 Organization 不等于自动拥有所有权限。**
> 你能写哪些仓库，取决于管理员在 LABA-Members 团队上挂了哪些仓库。
> 组织内未挂载到该团队的仓库，你依然没有写权限。
> 好处是：今后新增项目时管理员只需把仓库挂到团队上，**你无需重新申请**。

> [!IMPORTANT]
> 你**不需要 Fork** 本仓库。
> 你会以组织成员（通过团队授权）的身份直接向 `wustLABA/first-contributions` 推送自己的分支。

---

## 二、申请步骤

### 1. 打开申请页面

进入本仓库的 **Issues → New issue**，选择：

**「申请加入 wustLABA Organization」**

或直接访问：

<https://github.com/wustLABA/first-contributions/issues/new?template=laba-contribution-access.yml>

### 2. 勾选确认框，提交

页面上**只有一个需要你操作的地方**：勾选确认框。

> [!NOTE]
> 你**不需要**填写 GitHub 用户名、姓名、学号、班级或邮箱。
> GitHub 用户名由系统自动从你的账号读取，这也是为了不让你在公开页面暴露隐私。
> 也**绝不要**提交 GitHub Token、密码、身份证号等凭据类信息。

### 3. 等待机器人处理

提交后通常几秒内，机器人会在 Issue 中回复处理结果。

| 你会看到 | 含义 |
| --- | --- |
| Organization 加入申请已处理 | 首次申请成功，邀请已发送，请去接受 |
| 待接受的组织邀请（不会重复发送） | 你之前申请过且还没接受，请去接受邀请 |
| 你已经是 wustLABA 组织成员 | 你已在组织中，无需重复申请，机器人会继续检查你的团队归属 |

处理成功后，Issue 会被自动关闭并打上 `laba-access-approved` 标签。

### 4. 接受邀请

去以下任一位置接受邀请：

- **GitHub 网页** → 右上角通知铃铛 🔔
- **邮箱** → 查找来自 GitHub 的邀请邮件
- 直接访问：<https://github.com/orgs/wustLABA/invitation>

> [!WARNING]
> 没接受邀请之前，`git push` 会失败（`403 Permission denied`）。
> 这是最常见的卡点，请先确认邀请已接受。
>
> 另外：**接受组织邀请后可能还需要几秒到几分钟**，团队权限才会完全生效。
> 如果刚接受就 push 失败，请稍等片刻重试。

---

## 三、接受邀请之后：完成第一次贡献

```bash
# 1. 克隆仓库（注意：不是 fork，是直接 clone 官方仓库）
git clone https://github.com/wustLABA/first-contributions.git
cd first-contributions

# 2. 创建你自己的分支（分支名建议带上你的标识，避免与他人冲突）
git checkout -b laba/your-name

# 3. 创建你的报名文件
#    文件名请使用 docs/laba/ 下的约定格式，具体见仓库内说明
mkdir -p docs/laba
# 在你的编辑器里创建 docs/laba/<your-github-username>.md

# 4. 提交
git add .
git commit -m "docs: add <your-github-username> LABA registration"

# 5. 推送你的分支
git push -u origin laba/your-name
```

推送成功后，GitHub 会在终端输出里给出创建 Pull Request 的链接，
也可以直接访问：

<https://github.com/wustLABA/first-contributions/pulls>

点击 **New pull request**，选择你的分支作为来源，填写描述后提交即可。

---

## 四、常见问题

### `git push` 报 403 Permission denied

三种可能，按顺序排查：

1. **还没接受邀请** —— 见上面第 4 步，这是最常见原因。
2. **Push 到了错误的分支** —— 确保你推的是自己的分支，不是 `main`。
3. **凭据缓存问题** —— 清除旧凭据后重试：

   ```bash
   # Windows
   git credential-manager erase
   # 或删除 Windows 凭据管理器中的 github.com 条目
   ```

### 机器人没有回复

检查 Issue 是否带有 `laba-access-failed` 标签：

- **是** —— 说明自动授权失败，请等待 LABA 管理员人工处理，不要重复开新的 Issue。
- **否** —— 可能 Actions 尚未启用（仓库是 fork，首次需在 Actions 页面手动启用）。

### 我已经申请过一次，还能再申请吗？

可以，但**不会重复发送邀请**。机器人会识别到你已经有一条待接受的组织邀请，
然后提醒你去接受，而不是又发一条新的。

### 我已经在组织里了，又提交了一次申请

机器人会回复「你已经是 wustLABA 组织成员，无需重复申请」，不会报错，也不会重复邀请。
同时它会**继续检查你是否已在 LABA-Members 团队中**；如果不在，会自动把你补进去。

### 为什么我不能开一个普通 Issue 提问？

本仓库为了保持申请流程的可识别性，已关闭自由格式的空白 Issue。
如果你需要人工协助，请在已有相关 Issue 的评论区追问。

### 我能写哪些仓库？

你在 **LABA-Members 团队**当前已配置 Write 权限的那些仓库上都有写权限
（例如 `first-contributions`、`wustlaba-recruit`）。
查看方式：打开 <https://github.com/orgs/wustLABA/teams/laba-members/repositories>，
或在组织页面的 **Teams → LABA-Members → Repositories** 中查看。

没有列表里的仓库，你没有写权限 —— 这不是故障，请向管理员申请挂载。

---

## 五、给 LABA 管理员

### 前置条件

| 项目 | 要求 |
| --- | --- |
| Repository Issues | 必须**开启**（`Settings → General → Features → Issues`） |
| Actions | 必须**启用**。若本仓库是 fork，需在 `Actions` 页面点一次 "I understand my workflows, go ahead and enable them" |
| Organization | `wustLABA`，Token 所属账号需为组织 owner（或具备成员管理权限） |
| Team | `LABA-Members` 必须存在，且已挂载需要开放的仓库（Write） |
| Secrets | 必须配置 `LABA_REPO_ADMIN_TOKEN`（见下） |
| Labels | `laba-access`、`laba-access-approved`、`laba-access-failed` |

> [!IMPORTANT]
> **Team 的仓库权限由管理员在组织设置中配置，本 workflow 不碰。**
> 自动化只负责两件事：邀请用户加入组织、把用户加入 LABA-Members 团队。
> Team 上挂了哪些仓库、给什么权限级别，全部由管理员手工维护 ——
> 这正是「新增项目无需改 workflow」的原因。

创建标签（幂等，可重复执行）：

```bash
gh label create "laba-access"          --color "1f883d" --description "LABA 入组申请（由 Issue Form 自动添加）"
gh label create "laba-access-approved" --color "0e8a16" --description "组织邀请已发送且团队归属已同步"
gh label create "laba-access-failed"   --color "d73a4a" --description "自动处理失败，需管理员人工处理"
```

### 配置凭据（当前方案：Fine-grained PAT）

> [!CAUTION]
> **为什么不能用默认的 `GITHUB_TOKEN`？**
> 邀请用户加入 Organization 属于组织成员管理操作。
> GitHub 不允许 `GITHUB_TOKEN` 完成组织成员管理 —— 这不是配置问题，是平台限制。
> 因此必须使用外部凭据。请**不要**改成 `GITHUB_TOKEN` 让它「看起来能跑」，那样必然失败。

**步骤：**

1. 用一个对 `wustLABA` 组织有成员管理权限的账号，访问
   <https://github.com/settings/personal-access-tokens/new>

2. 按如下配置（**最小权限**，不要放宽）：

   | 配置项 | 值 |
   | --- | --- |
   | Resource owner | `wustLABA` ← 必须选组织，不能选个人账号 |
   | Repository access | 保留默认即可（组织邀请本身不需要仓库级权限） |
   | Repository permissions → **Administration** | **Read and write** |
   | Repository permissions → **Metadata** | **Read-only**（选中 Administration 后会自动带上） |
   | Organization permissions → **Members** | **Read and write** ← 邀请入组 + 加入 Team 必需 |
   | Expiration | 建议 ≤ 90 天，并记录到期日 |

   > [!NOTE]
   > **只有 `Members` 权限是不够的**：还需要能读取组织 Team 列表（用于解析
   > `LABA-Members` 的真实 slug）。如果调用 Team 相关接口时返回 403，
   > workflow 会明确报出 `TOKEN_PERMISSION_INSUFFICIENT` 并打 `laba-access-failed` 标签，
   > 不会假装成功。此时请检查 Token 是否为该组织所有（Resource owner 必须是 `wustLABA`）。

3. 生成后，把 token 值写入仓库 Secret：

   ```bash
   gh secret set LABA_REPO_ADMIN_TOKEN --repo wustLABA/first-contributions
   # 粘贴 token 后回车
   ```

   或网页操作：`Settings → Secrets and variables → Actions → New repository secret`
   名称填 `LABA_REPO_ADMIN_TOKEN`。

> [!NOTE]
> `Issues: write` 权限**不需要**授予这个 PAT。
> 发表评论、打标签、关闭 Issue 均由 Workflow 自身的 `GITHUB_TOKEN` 完成（见下方权限说明）。

### 权限设计（最小权限原则）

| Token | 用途 | 权限 |
| --- | --- | --- |
| `GITHUB_TOKEN`（自动提供） | 发评论、打标签、关闭 Issue | 仅 `issues: write` |
| `LABA_REPO_ADMIN_TOKEN` | 邀请入组、加入 Team、解析 Team slug | Repository `Administration: RW` + Organization `Members: RW` |

Workflow 文件顶部设置了 `permissions: {}`（默认全拒），
每个 job 只申请自己实际需要的权限，**不申请 `contents: write`**
（本 workflow 从不写代码，只做组织成员管理）。

### 安全措施

`LABA_REPO_ADMIN_TOKEN` 的保护方式：

- 只通过 `env:` 注入，**绝不**用 `${{ }}` 直接拼进 `run` 脚本 —— 避免表达式注入
- 绝不写入文件，绝不 `echo`
- 额外执行一次 `::add-mask::`，即使意外打印也会被替换成 `***`
- API 错误只记录 GitHub 返回的 `message` 字段，不回传请求头（避免日志中出现 auth 头）

### 防滥用机制

本仓库是公开仓库，任何人都能提交 Issue，因此做了以下防护：

| 风险 | 防护措施 |
| --- | --- |
| 普通 Issue 意外获得权限 | **三重校验**：标题前缀 `[LABA Access]` + `laba-access` 标签 + 正文含表单固定结构 |
| 手写标题冒充表单 | 校验正文必须包含表单渲染出的固定小节 `申请确认` |
| 不勾选确认框 | 必须存在勾选项；且确认小节内**有且仅有 1 个**任务项，防止伪造多行绕过 |
| 重复申请刷邀请 | 先查组织成员状态（active / pending），命中则只评论不重复邀请 |
| 同一 Issue 并发重复执行 | `concurrency` 按 issue number 串行化，且 `cancel-in-progress: false` |
| Bot 账号批量申请 | `user.type == 'Bot'` 或 login 以 `[bot]` 结尾 → 拒绝并回复失败 |
| 凭据泄露给不可信输入 | Token 与 Issue 内容在 Workflow 中完全隔离，不参与任何字符串拼接 |
| 静默失败 | 任何失败路径都会评论 + 打 `laba-access-failed` + **保持 Issue 开启** |
| 凭据越权 | 只申请 `issues: write`；不授予 `contents: write`，PAT 不授予 Issues 权限 |
| 权限不足被伪装成成功 | 403 明确映射为 `TOKEN_PERMISSION_INSUFFICIENT`，打 failed 标签且不关闭 Issue |

> [!NOTE]
> 关于防滥用的**残余风险**：本机制把用户加入 LABA-Members 团队，
> 因此任何通过校验的 GitHub 账号（只要不是 Bot）都能获得组织邀请，
> 进而获得该团队所挂载仓库的 Write 权限。
> GitHub 平台层面无法在此 Workflow 中可靠校验「是否是本校学生」。
>
> 当前阶段的应对：
> 1. 组织邀请以 **pending** 状态存在，管理员可在组织 People 页撤销；
> 2. 所有申请都留下公开 Issue 记录，可审计、可追溯；
> 3. 如需更强管控，应改为「管理员在 Issue 中手动打标签后才触发邀请」，
>    即把 `laba-auto-invite.yml` 的触发条件从 `opened` 改为 `labeled`。
>    这是后续可选的收紧方向，本阶段未启用，以保留「自助申请」体验。

### 工作流文件说明

| 文件 | 职责 |
| --- | --- |
| `.github/ISSUE_TEMPLATE/laba-contribution-access.yml` | 入组申请表单。标题固定 `[LABA Access]` 前缀，不收集任何隐私信息 |
| `.github/ISSUE_TEMPLATE/config.yml` | 关闭空白 Issue，提供文档与求助入口 |
| `.github/workflows/laba-sync-issue-labels.yml` | 为表单 Issue 补齐 `laba-access` 标签（**无凭据**，仅 `issues: write`） |
| `.github/workflows/laba-auto-invite.yml` | 校验申请 → 邀请加入组织 → 加入 Team → 评论 → 打标签 → 关闭 Issue |

> [!IMPORTANT]
> **本 workflow 不再调用任何仓库级授权接口。**
> 用户权限一律经由 Organization → Team → Repository 链路获得。

> [!IMPORTANT]
> **为什么标签要单独一个 Workflow？**
> GitHub 的已知行为：Issue Form 的 `labels:` 字段在 Issue **创建时不会自动应用**
> （见 [community discussion #150729](https://github.com/orgs/community/discussions/150729)）。
> 但授权 Workflow 需要「label + title 双重校验」，
> 所以用一个独立、不接触任何凭据的 Workflow 先把标签补上，形成闭环。
> 拆分的好处是：该 Workflow 即便被滥用，攻击面也仅限于「给公开 Issue 打个标签」。

### 后续迁移到 GitHub App（推荐长期方案）

当前使用 Fine-grained PAT 是因为它**部署最简单**。但它有两个固有缺点：

1. Token 是**长期有效**的，泄露后窗口期长；
2. 归属**个人账号**，该人离职或改密码后流程会中断。

GitHub App 是更合理的长期方案：installation token 有效期仅 **1 小时**，
且不依赖任何个人账号。迁移步骤如下：

1. 在 `wustLABA` 组织下创建 GitHub App：
   - `Settings → Developer settings → GitHub Apps → New GitHub App`
   - Homepage URL 填本仓库地址（必填但不影响功能）
   - **取消勾选** `Webhook → Active`（本方案不需要 Webhook）
   - Repository permissions → **Administration: Read and write**
   - Repository permissions → **Metadata: Read-only**
   - Organization permissions → **Members: Read and write** ← 邀请入组 + 加入 Team 必需
   - Where can this app be installed → `Only on this account`

2. 生成 Private Key，记录 App ID。

3. 把 App 安装到 `wustLABA` 组织（需覆盖 `first-contributions`）。

4. 写入两个 Secret：

   ```bash
   gh secret set LABA_APP_ID          --repo wustLABA/first-contributions
   gh secret set LABA_APP_PRIVATE_KEY --repo wustLABA/first-contributions
   # 第二个粘贴 .pem 全文
   ```

5. 修改 `laba-auto-invite.yml`：在 `邀请加入组织并同步 Team` 步骤前插入一个换取 token 的步骤，
   然后把 `env.ADMIN_TOKEN` 替换为它的输出：

   ```yaml
   - name: 获取 GitHub App 安装令牌
     id: app-token
     uses: actions/create-github-app-token@v1
     with:
       app-id: ${{ secrets.LABA_APP_ID }}
       private-key: ${{ secrets.LABA_APP_PRIVATE_KEY }}
       owner: wustLABA
       repositories: first-contributions
   ```

   ```yaml
   # 原：ADMIN_TOKEN: ${{ secrets.LABA_REPO_ADMIN_TOKEN }}
   ADMIN_TOKEN: ${{ steps.app-token.outputs.token }}
   ```

6. 删除 `LABA_REPO_ADMIN_TOKEN` Secret，确认流程正常后移除 PAT。

### 故障排查

| 现象 | 排查方向 |
| --- | --- |
| Issue 创建后 Workflow 未触发 | Actions 是否启用（fork 需手动启用）；Workflow 是否在默认分支上 |
| 无评论、无标签 | `laba-sync-issue-labels.yml` 是否执行；标签是否已创建 |
| 日志出现 `TOKEN_PERMISSION_INSUFFICIENT` | PAT 缺少 Organization `Members: RW`，或 Resource owner 不是 `wustLABA` |
| 日志出现 `TEAM_NOT_FOUND` | 组织内没有名为 `LABA-Members` 的 Team，或 PAT 看不到该 Team |
| 反复 `laba-access-failed` 且 comment 提到团队同步失败 | Team 成员关系写入失败，检查 PAT 的 Organization 权限与 Team 可见性 |
| 用户接受邀请后仍无写权限 | Team 是否已挂载目标仓库；权限生效可能有数分钟延迟 |
| 日志出现 `HTTP 404`（查询成员关系） | 正常路径：说明该用户尚未加入组织，Workflow 会继续发起邀请 |
| 日志出现 `Resource not accessible by integration` | 说明用了 `GITHUB_TOKEN` 而不是 PAT，检查 `ADMIN_TOKEN` 注入 |

排查时可在 Actions 日志中搜索 `::error::` 与 `core.error` 的输出，
它们只包含错误码、HTTP 状态码和 GitHub 的 `message`，**不包含**任何 token 内容。

### 遗留的管理员职责

自动流程**只负责邀请入组并把用户加入 Team**。以下仍需人工或后续功能完成：

- 报名信息收集与校验（本阶段不做）
- LABA-Members 团队挂载哪些仓库、给什么权限级别（由管理员在组织设置中维护）
- PR 内容审核与合并（`auto-pr-merge.yml` 已有基础自动合并逻辑）
- 撤销误发/恶意的组织成员资格或团队归属
- 定期轮换 PAT（建议设置日历提醒，与 Expiration 对齐）

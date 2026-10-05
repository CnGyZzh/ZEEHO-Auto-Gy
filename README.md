<div align="center">

# ZEEHO Auto Gy

**极核 ZEEHO · GitHub Actions 自动任务**

[![Profile](https://img.shields.io/badge/CnGyZzh-Gy-181717?logo=github)](https://github.com/CnGyZzh)
[![Level](https://img.shields.io/badge/Hub-Level-6f42c1)](https://github.com/CnGyZzh/Level)
[![Actions](https://img.shields.io/badge/GitHub_Actions-Auto-2088FF?logo=githubactions)](https://github.com/CnGyZzh/ZEEHO-Auto-Gy/actions)

</div>

## 功能

- 每日自动签到
- 自动执行社区积分任务：发帖、点赞、评论、分享
- 完成后删除临时动态
- 满足条件时自动尝试盲盒奖励
- 成功后发送**任务明细邮件**
- Token / userId / SMTP 凭据全部使用 GitHub Actions Secrets
- 支持手动运行

## Schedule

当前定时：**北京时间每天 10:00**

GitHub Actions cron 使用 UTC，因此工作流配置为 0 2 * * *。平台负载较高时可能延迟几分钟。

## Upstream

任务逻辑复用 [cluck798/ZEEHO](https://github.com/cluck798/ZEEHO) 的 script/zeeho.js，并固定到指定 commit，避免上游突然更新影响每日任务。

## Required secrets

| Secret | 用途 |
| :--- | :--- |
| ZEEHO_TOKEN | ZEEHO authorization token |
| ZEEHO_USER_ID | baseInfo_v2 返回的 data.id |
| SMTP_SERVER | SMTP 地址，例如 smtp.yeah.net |
| SMTP_PORT | SSL SMTP 常用 465 |
| SMTP_USERNAME | 发件邮箱 |
| SMTP_PASSWORD | 邮箱客户端授权码 |
| MAIL_TO | 收件邮箱 |

可选：

- ZEEHO_USER_NAME：日志名称，默认 Gy
- ZEEHO_USER_AGENT：默认 okhttp/4.12.0

> 不要把 Token、邮箱密码或授权码写进 README、Issues、源码或普通变量。

## Run

Actions → **ZEEHO Auto Gy** → **Run workflow**。

正常日志会包含签到、连续签到天数、互动任务、盲盒状态、积分汇总以及邮件发送步骤。

## Navigation

**[CnGyZzh](https://github.com/CnGyZzh)** · **[Level](https://github.com/CnGyZzh/Level)** · **[HyperMax](https://github.com/CnGyZzh/HyperMax)** · **[WeType Monet](https://github.com/CnGyZzh/WeType_Monet-Gy)**

---

<sub>仅用于个人自动化。接口、风控或平台规则变化时应及时停用并重新核对。</sub>

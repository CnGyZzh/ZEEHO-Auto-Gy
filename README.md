# ZEEHO-Auto-Gy

极核 ZEEHO 自动任务的 GitHub Actions 封装。

## 功能

- 每日自动签到
- 自动执行上游支持的社区积分任务：发帖、点赞、评论、分享
- 任务完成后删除本次临时动态
- 达到上游判定条件后自动尝试盲盒奖励
- 支持 GitHub Actions 手动运行
- Token / userId 只通过 GitHub Actions Secrets 注入，不写入仓库
- 默认北京时间每天约 07:07 执行

## 来源与版本

任务逻辑复用 `cluck798/ZEEHO` 的 `script/zeeho.js`，固定到：

`a73a500856e22de8aa56bf98d59aff2dc0d2a84d`

这样不会因为上游仓库突然更新导致第二天行为改变。

## 必填 Secrets

进入你的仓库：

`Settings -> Secrets and variables -> Actions -> New repository secret`

创建：

### 1. ZEEHO_TOKEN

Reqable 请求头里的 `authorization`。

可以填写完整的：

`bearer xxxxxxxx`

也可以只填写 token 本体。工作流会自动清理 `Bearer/bearer` 前缀。

### 2. ZEEHO_USER_ID

Reqable `baseInfo_v2` 响应中的：

`data.id`

## 可选 Secrets

### ZEEHO_USER_NAME

日志显示名称。不填默认 `Gy`。

### ZEEHO_USER_AGENT

不填默认：

`okhttp/4.12.0`

与你提供的 ZEEHO 3.0.5 抓包一致。

## 第一次测试

1. 上传本项目全部文件到你自己的 GitHub 仓库。
2. 添加上面的两个必填 Secrets。
3. 打开 `Actions`。
4. 选择 `ZEEHO Auto Gy`。
5. 点 `Run workflow`。
6. 等待运行完成并打开日志。

正常情况下日志会出现签到、连续签到天数、互动任务、盲盒状态和今日积分汇总。

## 安全

- 不要把 Token 写进 README、Issues、源码或 Actions 普通变量。
- 不要把 `account.json` 提交到仓库。
- 如果极核重新登录后 Token 失效，重新从 Reqable 获取，并只更新 `ZEEHO_TOKEN` Secret。
- 第三方自动化可能触发服务端风控；接口或规则变化时应停止运行并重新核对。

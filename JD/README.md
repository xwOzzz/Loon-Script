# JD — 京东定时任务配置

本目录收集京东相关的 Loon 定时任务配置（.conf）：共 65 条定时任务与 5 条请求/响应规则，脚本均指向 ChuheGit/1 仓库的 jd_scripts 目录。覆盖京豆签到与领取、东东农场/工厂/超市/萌宠等互动玩法、宠汪汪系列、直播与红包活动，以及资产变动通知、保价、取关等管理类任务；另附带一条小米运动任务。

## 使用方法

1. 在 Loon 中进入 **配置 → 脚本 → 订阅脚本**，点右上角 + 号添加订阅链接（文件头原说明）。
2. **先获取 Cookie 再跑定时任务**：京东签到 Cookie 的获取见 [Cookie/JD-Get-Cookie.conf](../Cookie/JD-Get-Cookie.conf)——Safari 打开京东网页登录后触发签到请求抓取（请勿在京东 APP 内获取）；网页 Cookie 有效期最长 31 天，失效后需重复上述步骤。
3. **多账号 Cookie 规则默认禁用**：文件内「获取多账号京东 Cookie」一条 http-request 规则的 `enable=false`，有需要时再手动启用。
4. **宠汪汪助力需配合请求规则**：文件内另有 3 条针对 draw.jdfcloud.com 的请求/响应规则，负责助力与 Token 更新（`requires-body=true`），删除定时任务时请勿误删这几条规则。
5. MITM 主机名共 4 个：me-api.jd.com、draw.jdfcloud.com、jdjoy.jd.com，以及小米运动登录用的 account.huami.com。

## 文件索引

| 文件 | 说明 | 来源 |
|---|---|---|
| JD.conf | 京东定时任务配置：65 条 cron 定时任务（京豆、农场、工厂、超市、萌宠、宠汪汪、直播、红包等）+ 5 条 http-request/http-response 规则（多账号 Cookie 获取、宠汪汪助力与 Token 更新、小米运动登录 Token 获取） | [ChuheGit/1](https://github.com/ChuheGit/1) |

> **免责声明**：本目录所有配置均整理自互联网公开资源，仅供学习交流；因软件版本迭代与规则时效性，部分内容可能已失效，能否正常使用请自行测试。

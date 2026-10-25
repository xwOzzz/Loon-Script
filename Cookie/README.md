# Cookie — Cookie 获取配置

本目录收集 Loon 的 Cookie 获取配置（.conf），用于定时签到脚本在首次使用前抓取各平台 Cookie，抓取完成后应及时禁用，只保留定时任务。

## 使用方法

1. 在 Loon 中进入 **配置 → 订阅 → 脚本 → 添加订阅**，填入对应配置文件的 raw 链接。
2. 按文件内注释的步骤触发一次请求，获取 Cookie（一般是打开对应 App 或网页完成一次签到/登录）。
3. **获取完 Cookie 后，记得把 Cookie 获取部分禁用或删除**，只保留定时任务，避免重复抓包和不必要的 MITM。

## 文件索引

| 文件 | 说明 | 来源 |
|---|---|---|
| Get-Cookie.conf | 定时签到脚本的 Cookie 获取合集，集成 NobyDa、Chavy 及个人收集的常用签到脚本，覆盖中国移动、中国联通、中国电信、贴吧、网易云音乐等平台 | [Tartarus2014/Script](https://github.com/Tartarus2014/Script) |
| JD-Get-Cookie.conf | 京东签到 Cookie 获取：Safari 打开京东网页登录后触发签到请求抓取（请勿在京东 APP 内获取）；网页 Cookie 有效期最长 31 天，失效后需重复上述步骤；签到脚本默认每天 0:05 执行 | [NobyDa/Script](https://github.com/NobyDa/Script) |

> **免责声明**：本目录所有配置均整理自互联网公开资源，仅供学习交流；因软件版本迭代与规则时效性，部分内容可能已失效，能否正常使用请自行测试。

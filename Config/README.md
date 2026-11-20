# Config — Loon 通用配置

本目录收集 Loon 全量配置（.conf）与定时任务合集：四份 Tartarus2014 全量配置（SD-CN.conf / URL-Test.conf / DualSubs.conf / Lite.conf）与一份定时任务配置（Task.conf），均整理自 [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script)。

## 使用方法

1. **全量配置四选一**：SD-CN.conf、URL-Test.conf、DualSubs.conf、Lite.conf 导入一份即可，不要多份混用；四份配置的 `[Remote Proxy]` 都已填一条短链订阅（suo.yt/W7BkpTS），导入后按需替换为自己的机场订阅链接，再更新订阅规则。
2. **安装并信任证书**：配置 → 证书管理 → 生成新的 CA 证书，之后进入「设置」>「通用」>「描述文件」安装 Loon 的证书，并在「设置」>「通用」>「关于本机」>「证书信任设置」开启对 Loon 证书的信任（四份配置头注释原说明）。
3. **网易云音乐解锁（仅 SD-CN / URL-Test）**：需用 Safari 访问 https://cdn.jsdelivr.net/gh/nondanee/UnblockNeteaseMusic@master/ca.crt ，下载并安装「UnblockNeteaseMusic Root CA」，再开启信任；解锁节点订阅为 https://git.io/JfNq3（文件头原说明）。
4. **Task.conf 单独导入**：149 条 cron 定时任务默认全部关闭（`enable=false`），按需逐条开启；取 Cookie 类任务跑完后记得关闭。
5. **注意失效的上游引用（2026-11-20 核实）**：SD-CN / URL-Test / Lite 的 `[Remote Script]` 段引用的上游 `Tartarus2014/Loon-Script` master 根目录路径（Fake_Vip.conf、Cookie.conf、Task.conf、Script.conf、JD.conf），以及四份配置 `[Plugin]` 段引用的 `Plugin/Unlock/TikTokJP.plugin`、`Plugin/MediaCheck.plugin`、`Plugin/TF-Download.plugin`，均已返回 404——上游已重组为 Config/、JS/、Plugin/（.lpx）、Rule/ 目录（2026-11-15 更新），旧 .conf / .plugin 路径不复存在；导入后这些引用会失效，可按需改成本仓库对应文件（Cookie/、JD/、Config/、Plugin/ 目录下均有）或上游新路径。DualSubs 的两个双字幕插件引用也已 404：该项目已更名为 DualSubs/Universal 并重构为源码仓库，旧 plugin/ 路径不存在。Lite 唯一的远程规则（DivineEngine Advertising.list）同样 404，该仓库已不存在，导入后去广告规则为空，需自行补一条可用的去广告规则。blackmatrix7 的远程规则与插件链接、chavyleung 的 BoxJs 插件链接核实仍可用。

## 文件索引

| 文件 | 说明 | 来源 |
|---|---|---|
| SD-CN.conf | Loon 全量配置（by Tartarus）：完整策略组（FINAL / 节点选择 / 苹果服务 / 网易音乐 / 奈飞视频 / 油管视频 / 巴哈姆特 / 电报消息 / 国外媒体 / 港台番剧，另有香港 / 台湾 / 狮城 / 韩国 / 日本 / 美国 6 个地区节点组与解锁节点），13 条远程规则（blackmatrix7），默认直连、策略组手动开启；含网易云音乐解锁说明 | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |
| URL-Test.conf | 与 SD-CN.conf 结构相同：14 条远程规则（多 1 条 Advertising_Domain.list）；6 个地区节点组为 `url-test`（http://www.qualcomm.cn/generate_204，每 600 秒测速自动选最快节点）；BoxJs 插件为 `.tf` 版 | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |
| DualSubs.conf | 与 SD-CN.conf 同源：12 条远程规则，无网易音乐策略组与解锁节点；新增 DualSubs 双字幕插件（流媒体版 + YouTube 版，默认关闭）与 BoxJs 订阅地址，图标来自 QureIconSet / Orzmini；`[Rule]` 有一条 api.waqi.info 走日本节点 | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) / [DualSubs](https://github.com/DualSubs/Universal) |
| Lite.conf | 精简版全量配置：`[Proxy Group]` 为空（无自带策略组），仅 1 条远程规则（DivineEngine Advertising.list，REJECT——该链接已失效，见上）；本地规则只有 GEOIP,CN,DIRECT 与 FINAL,PROXY；MITM、`[URL Rewrite]` 与 `[Script]` 均关闭；插件 7 个（含 TikTokJP、Advertising、MediaCheck、TF-Download、Redirect、BoxJs，Sub-Store 订阅解析器默认关闭） | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |
| Task.conf | 定时任务合集：149 条 cron，全部默认关闭；分 5 组——Boxjs 维护 2 条（Tartarus）、Evilbutcher 签到类 9 条（NASA 每日一图、iDaily、App 价格监控、热门监控、微博超话、GLaDOS / 机场签到、Funboat）、zZPiglet 6 条（微博通知、欧可林、豆瓣电影日历、Alipay、航旅纵横）、NobyDa 6 条（京东、爱奇艺、吾爱破解签到）、chavyleung 段 126 条（多位作者脚本合集） | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |

> **免责声明**：本目录所有配置均整理自互联网公开资源，仅供学习交流；因软件版本迭代与规则时效性，部分内容可能已失效，能否正常使用请自行测试。

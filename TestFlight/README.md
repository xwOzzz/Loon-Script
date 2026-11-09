# TestFlight — TestFlight 相关配置

本目录收集 TestFlight 相关的 Loon 配置（.conf）：两份全量 Loon 配置（TF-CN.conf / TF-CN-v2.conf，均出自 Tartarus2014）与一份 TestFlight 区域限制解除配置（Download.conf）。

## 使用方法

1. **全量配置二选一**：导入 TF-CN.conf 或 TF-CN-v2.conf，两者内容基本一致——v2 去掉了作者署名头，并把 `[URL Rewrite]` 改为新版 Loon 语法的 `[Rewrite]` 段名；其余分流策略组、远程规则、远程脚本与插件引用均相同。导入后添加机场订阅链接，再更新订阅规则。
2. **安装并信任证书**：配置 → 证书管理 → 生成新的 CA 证书，之后进入「设置」>「通用」>「描述文件」安装 Loon 的证书，并在「设置」>「通用」>「关于本机」>「证书信任设置」开启对 Loon 证书的信任（两份配置头注释原说明）。
3. **Download.conf 已弃用**：文件头注明该 URL 将在一段时间后删除，.conf 后缀请改用 .plugin——请改用 [Plugin/TF-Download.plugin](../Plugin/TF-Download.plugin)。其脚本为 NobyDa 的 TF_Download.js，拦截 testflight.apple.com 的安装请求以解除区域限制，需 MITM testflight.apple.com，iosapps.itunes.apple.com 跳过代理。
4. **注意旧引用路径**：两份全量配置的 [Remote Script] / [Plugin] 段引用的仍是 Tartarus2014 上游 master 的旧路径（如 master/Fake_Vip.conf），与本仓库重组后的目录结构不一致，导入后请按需调整。

## 文件索引

| 文件 | 说明 | 来源 |
|---|---|---|
| TF-CN.conf | Loon 全量配置（by Tartarus）：完整分流策略组、远程规则（去广告 / Apple / 网易云音乐 / YouTube / Netflix / Bahamut / Telegram / TestFlight 等）、远程脚本与插件引用；`[URL Rewrite]` 为旧写法 | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |
| TF-CN-v2.conf | 与 TF-CN.conf 内容基本一致：去掉作者署名头，`[URL Rewrite]` 改为新版 `[Rewrite]` 段名 | [Tartarus2014/Loon-Script](https://github.com/Tartarus2014/Loon-Script) |
| Download.conf | TestFlight 区域限制解除：http-request 拦截 testflight.apple.com 安装请求，调用 NobyDa 的 TF_Download.js；⚠️ 文件头注明已弃用，请改用 Plugin/TF-Download.plugin | [NobyDa（gist）](https://gist.githubusercontent.com/NobyDa/9be418b93afc5e9c8a8f4d28ae403cf2) |

> **免责声明**：本目录所有配置均整理自互联网公开资源，仅供学习交流；因软件版本迭代与规则时效性，部分内容可能已失效，能否正常使用请自行测试。

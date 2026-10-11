# impad pro

在手机上实现平板登录的 Xposed 模块。将手机伪装成平板设备，绕过「仅限平板端登录」的限制。

> 本仓库仅用于分发（Release + APK），源代码在 [SymonChu/I-Am-Pad](https://github.com/SymonChu/I-Am-Pad)。
> 基于 [I-Am-Pad](https://github.com/Houvven/I-Am-Pad)（libxposed API）二次开发，遵循 GPL-3.0。

## 支持应用（11 个）

| 应用 | 包名 | 实现方式 |
|---|---|---|
| 微信 | `com.tencent.mm` | hook `CgiCheckLoginAsPad` + `isFoldableDevice` |
| QQ | `com.tencent.mobileqq` | hook `PadUtil` 平板判定 + 平板属性模拟 |
| TIM | `com.tencent.tim` | 复用 QQ 同款平板伪装 |
| 企业微信 | `com.tencent.wework` | hook `isAndroidPad*` 返回平板 |
| 钉钉 | `com.alibaba.android.rimet` | hook `isMultipleLoginFoldable` |
| 小红书 | `com.xingin.xhs` | `getDeviceType=pad` + 精确型号 |
| 拼多多 | `com.xunmeng.pinduoduo` | hook 平板判定方法（移植 TabletHook PddHook）|
| 国航之翼 | `com.airchina.wecompro` | 企微定制 `WwUtil.isPadJudge` |
| 粤政易 | `com.zwfw.YueZhengYi` | 企微定制 `WwUtil.isPadJudge` |
| 中电建 | `cn.powerchina.pact` | 企微定制 `WwUtil.isPadJudge` |
| 中建 | `com.cscec.portal` | 企微定制 `WwUtil.isPadJudge` |

## 安装使用

**LSPosed 模式**（需要 LSPosed 框架）

1. 安装 APK
2. 在 LSPosed 管理器中启用本模块，并勾选需要模拟的应用作用域
3. 重启对应应用生效

**Zygisk 模式**（Magisk 启用 Zygisk / KernelSU，免 LSPosed 框架）

刷入 `impad.pro-zygisk-<版本>.zip`，重启后对所有宿主生效（native 全量注入，作用域由模块内置白名单把关）。

## 说明

- 各应用的平板判定实现会随应用版本更新而变化，若某应用更新后失效，请到源代码仓库提交 issue
- 本项目仅供学习交流，请遵守相关应用的用户协议

## 致谢

- [I-Am-Pad](https://github.com/Houvven/I-Am-Pad)（原 `com.houvven.impad`）— 平板登录伪装核心，微信/QQ/钉钉/企业微信/小红书等宿主实现源自上游
- [TabletHook](https://github.com/roro2239/TabletHook) — 拼多多的平板判定与诊断钩子移植自该项目

## License

[GPL-3.0](https://github.com/SymonChu/I-Am-Pad/blob/master/LICENSE)

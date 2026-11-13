# 渴瘾 Vorax Solver · Android 移植研究

> **状态：第一阶段开发中（2026-11-13）**  
> 本仓库是独立的公开上游来源与进度记录仓库，**不是火炬AI助手 Android APP 的源码仓库，也不提供 APK**。仓库名称 `v1.3.9` 不代表当前 Android 软件版本。

## 项目目标

研究将 Torchlight: Infinite「渴瘾 / Surgical Preparation」玩法的开源 Rust 求解器移植至 Android ARM64。工具只读取游戏画面与获准读取的游戏日志，并向玩家提供建议；**不自动点击、按键或操作游戏**。

## 公开上游与许可证

- 上游项目：[DinoRaos/vorax-solver-rs](https://github.com/DinoRaos/vorax-solver-rs)
- 固定研究基线：[699789727e560ff6917a4487a6e66c0fe34a4d90](https://github.com/DinoRaos/vorax-solver-rs/commit/699789727e560ff6917a4487a6e66c0fe34a4d90)
- 上游开源许可证：[MIT LICENSE](https://github.com/DinoRaos/vorax-solver-rs/blob/699789727e560ff6917a4487a6e66c0fe34a4d90/LICENSE)
- 上游限制与开发规则：[AGENTS.md](https://github.com/DinoRaos/vorax-solver-rs/blob/699789727e560ff6917a4487a6e66c0fe34a4d90/AGENTS.md)

上游版权归 DinoRaos、tidewarden、Moebing 等相应权利人所有。仅可使用有明确授权的上游版本；不得从 tidewarden 在 2026-10-22 MIT 许可基线之后的受限制版本引入代码。游戏画面或第三方资源是否允许再分发，仍需逐项确认。

## 开发进度

| 阶段 | 状态 |
| --- | --- |
| 上游项目选型、代码结构及许可初审 | 已完成初审 |
| Android ARM64 原生库与调用接口 | Rust C ABI 与独立 .NET 调用层源码已提交开发分支；编译和运行尚未验证 |
| 渴瘾独立画面识别 / S13-KYZ 事件解析 | 尚未实施 |
| 手机版推荐坐标映射、结果过期保护 | 尚未实施 |
| Android 16 实机准确率、性能与耗电验证 | 尚未实施 |
| 可交付 APK / 正式版本发布 | 尚未实施 |

**不以代码提交代替编译、单元测试或实机验收。** 只有得到真实测试记录才更新阶段状态。

## 仓库公开边界

本仓库只允许存放经许可核对的**公开上游源码及资源**、原始许可证，以及独立撰写的公开进度文档。禁止上传任何非公开 Android APP 源码、私有模型及素材、调试截图/日志、个人数据、秘钥、签名证书、构建密钥及私有 Git 历史。

首个提交仅初始化公开文档；上游文件待按固定提交和版权白名单完成核验后再导入。**不得从任何私有工程分支推送或合并到本仓库。**

## 免责声明

非游戏官方项目，与游戏开发及发行方无关联。原游戏名称、图像等权利归相应权利人所有。

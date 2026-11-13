# 渴瘾 Vorax Solver · Android 移植研究

> **状态：第一阶段 ARM64 编译及宿主机桥接测试已通过，待 Android 实机验证（2026-11-13）**  
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
| 上游项目选型、代码结构及许可初审 | 已完成初审，研究基线固定 |
| Android ARM64 原生库与调用接口 | 已核实云端构建成功并产出 AArch64 ELF 动态库（Android API 34 / NDK r27c）；**尚未验证安卓设备运行** |
| 渴瘾独立画面识别 / S13-KYZ 事件解析 | 尚未实施 |
| 手机版推荐坐标映射、结果过期保护 | 尚未实施 |
| Android 16 原生运行探针 | 独立调试 APK 工程源码已建立；待云端构建、签名检查与手机安装测试 |
| Android 16 实机准确率、性能与耗电验证 | 尚未实施；探针仅使用合成单卡牌局面 |
| 可交付 APK / 正式版本发布 | 尚未实施 |

**不以代码提交代替编译、单元测试或实机验收。** 只有得到真实测试记录才更新阶段状态。


## 第一阶段验证记录（2026-11-13）

根据提交的云端构建日志及独立检查的 Android 动态库 ELF：

- 固定上游提交：`699789727e560ff6917a4487a6e66c0fe34a4d90`；Rust 上游测试 **8/8** 通过。
- Rust FFI 验证 **6/6** 通过，包含取消、非法 JSON、未知卡牌与真实建议调用。
- .NET 10 / Linux x86_64 → Rust 宿主机跨语言 Smoke **3 项检查通过**。
- `aarch64-linux-android` 原生库构建退出码为 **0**；独立检查确认为 Android API 34、ARM64 AArch64 ELF，六个 ABI 接口符号存在。
- **未完成：** Android 16 手机上的实际 `dlopen` / P/Invoke、线程取消时延、连续求解、发热耗电与实际画面识别验证。

上述记录只说明第一阶段云端构建和宿主机测试结果，不代表 Android APP 已成功集成或发布。

## 仓库公开边界

本仓库只允许存放经许可核对的**公开上游源码及资源**、原始许可证，以及独立撰写的公开进度文档。禁止上传任何非公开 Android APP 源码、私有模型及素材、调试截图/日志、个人数据、秘钥、签名证书、构建密钥及私有 Git 历史。

首个提交仅初始化公开文档；上游文件待按固定提交和版权白名单完成核验后再导入。**不得从任何私有工程分支推送或合并到本仓库。**

## 免责声明

非游戏官方项目，与游戏开发及发行方无关联。原游戏名称、图像等权利归相应权利人所有。

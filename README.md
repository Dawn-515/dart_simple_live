> ### ⚠ 本项目不提供Release安装包，请自行编译后运行测试。


<p align="center">
    <img width="128" src="/assets/logo.png" alt="Simple Live logo">
</p>
<h2 align="center">Simple Live</h2>

<p align="center">
简简单单的看直播
</p>

![浅色模式](/assets/screenshot_light.jpg)

![深色模式](/assets/screenshot_dark.jpg)

## 支持直播平台：

- 虎牙直播

- 斗鱼直播

- 哔哩哔哩直播

- 抖音直播

## APP支持平台

- [x] Android
- [x] iOS
- [x] Windows `BETA`
- [x] MacOS `BETA`
- [x] Linux `BETA`
- [x] Android TV `BETA`

## 项目结构

- **`simple_live_core`** 项目核心库，实现获取各个直播平台的信息及弹幕。
  - 支持虎牙、斗鱼、B站、抖音四大平台
  - 提供统一的接口设计
  - 支持直播搜索、分类、播放、弹幕等功能
  
- **`simple_live_console`** 基于 `simple_live_core` 的命令行控制台程序。
  - 快速获取直播链接
  - 实时弹幕监控
  - 适合服务器环境和自动化脚本
  
- **`simple_live_app`** 基于核心库实现的 Flutter 移动端/桌面端客户端。
  - 支持 Android、iOS、Windows、macOS、Linux
  - 完整的直播观看体验
  - 支持关注、同步、账号登录等功能
  
- **`simple_live_tv_app`** 基于核心库实现的 Flutter Android TV 客户端。
  - 专为电视大屏优化
  - 完美支持遥控器操作
  - Leanback 风格设计

## 环境

Flutter : `3.38`

### 使用 FVM 管理 Flutter 版本（推荐）

本项目使用 FVM (Flutter Version Management) 来管理 Flutter 版本，确保开发环境一致性。

#### 安装 FVM

```bash
# 使用 Dart pub 安装
dart pub global activate fvm

# 或使用 Homebrew (macOS)
brew tap leoafarias/fvm
brew install fvm
```

#### 项目配置

在 `simple_live_app` 目录下已配置 `.fvmrc` 文件，指定了项目使用的 Flutter 版本。

#### 常用命令

**进入项目目录**：
```bash
cd simple_live_app
```

**安装依赖**：
```bash
fvm flutter pub get
```

**运行项目**：
```bash
fvm flutter run
```

**构建项目**：
```bash
# Android
fvm flutter build apk

# iOS
fvm flutter build ios

# Windows
fvm flutter build windows

# macOS
fvm flutter build macos

# Linux
fvm flutter build linux
```

**清理构建缓存**：
```bash
fvm flutter clean
```

> **注意**：所有 Flutter 相关命令都需要加上 `fvm` 前缀，例如 `fvm flutter doctor`、`fvm flutter analyze` 等。

## 快速开始

### 移动端/桌面端应用 (simple_live_app)

```bash
cd simple_live_app
fvm flutter pub get
fvm flutter run
```

### TV 应用 (simple_live_tv_app)

```bash
cd simple_live_tv_app
flutter pub get
flutter run
```

### 控制台程序 (simple_live_console)

```bash
cd simple_live_console
dart pub get

# 直接运行
dart run bin/simple_live_console.dart -i https://live.bilibili.com/23058

# 或编译后运行
dart compile exe bin/simple_live_console.dart -o simple_live.exe
./simple_live.exe -i https://live.bilibili.com/23058
```

## 功能特性

### 核心功能

- ✅ 多平台直播聚合（虎牙、斗鱼、B站、抖音）
- ✅ 直播间搜索（房间/主播）
- ✅ 分类浏览
- ✅ 多清晰度选择
- ✅ 实时弹幕显示
- ✅ 弹幕自定义（透明度、大小、速度等）
- ✅ 礼物消息
- ✅ SuperChat/醒目留言

### 用户功能

- ✅ 关注主播
- ✅ 观看历史
- ✅ 收藏管理
- ✅ 多设备同步（WebDAV/SignalR）
- ✅ B站/抖音账号登录

### 播放功能

- ✅ 多种清晰度（原画、蓝光、超清等）
- ✅ 全屏播放
- ✅ 画中画 (PIP)
- ✅ 屏幕旋转控制
- ✅ 亮度和音量调节
- ✅ 屏幕常亮

### 界面功能

- ✅ 明暗主题
- ✅ 动态取色 (Material You)
- ✅ TV 遥控器支持
- ✅ 国际化支持

## 架构设计

项目采用分层架构设计：

```
┌─────────────────────────────────────┐
│      应用层 (UI Applications)       │
│  simple_live_app / simple_live_tv_app│
├─────────────────────────────────────┤
│    业务层 (Business Logic)          │
│   Controllers / Services / Models   │
├─────────────────────────────────────┤
│      核心层 (Core Library)          │
│       simple_live_core              │
├─────────────────────────────────────┤
│      平台接口 (Site Interface)       │
│  Huya / Douyu / Bilibili / Douyin  │
└─────────────────────────────────────┘
```

## 参考及引用

[AllLive](https://github.com/xiaoyaocz/AllLive) `本项目的C#版，有兴趣可以看看`

[dart_tars_protocol](https://github.com/xiaoyaocz/dart_tars_protocol.git)

[wbt5/real-url](https://github.com/wbt5/real-url)

[lovelyyoshino/Bilibili-Live-API](https://github.com/lovelyyoshino/Bilibili-Live-API/blob/master/API.WebSocket.md)

[IsoaSFlus/danmaku](https://github.com/IsoaSFlus/danmaku)

[BacooTang/huya-danmu](https://github.com/BacooTang/huya-danmu)

[TarsCloud/Tars](https://github.com/TarsCloud/Tars)

[YunzhiYike/douyin-live](https://github.com/YunzhiYike/douyin-live)

[5ime/Tiktok_Signature](https://github.com/5ime/Tiktok_Signature)

## 贡献指南

欢迎贡献代码、报告问题或提出建议！

### 如何贡献

1. Fork 本仓库
2. 创建你的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的修改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

### 报告问题

如果你发现了问题，请在 [Issues](https://github.com/xiaoyaocz/dart_simple_live/issues) 页面提交，并包含以下信息：

- 问题描述
- 复现步骤
- 预期行为
- 实际行为
- 设备信息（操作系统、应用版本等）

## 常见问题 (FAQ)

### Q: 为什么没有提供 Release 安装包？

A: 本项目仅用于学习交流，请自行编译后使用。

### Q: 支持哪些直播平台？

A: 目前支持虎牙直播、斗鱼直播、哔哩哔哩直播、抖音直播。

### Q: 如何同步多设备数据？

A: 支持两种同步方式：
- WebDAV: 支持各类 WebDAV 服务（如坚果云、ownCloud等）
- SignalR: 支持 SignalR 服务器实时同步

### Q: 支持登录账号吗？

A: 支持 B站和抖音的扫码登录，登录后可获取关注列表。

### Q: TV 版和移动版有什么区别？

A: TV 版专为电视大屏优化，支持遥控器操作，界面采用 Leanback 风格设计。

## 相关项目

- [simple_live](https://github.com/xiaoyaocz/simple_live) - 原 C# 版本
- [AllLive](https://github.com/xiaoyaocz/AllLive) - C# 版本直播应用

## 声明

本项目的所有功能都是基于互联网上公开的资料开发，无任何破解、逆向工程等行为。

本项目仅用于学习交流编程技术，严禁将本项目用于商业目的。如有任何商业行为，均与本项目无关。

如果本项目存在侵犯您的合法权益的情况，请及时与开发者联系，开发者将会及时删除有关内容。

## Star History

<a href="https://www.star-history.com/#xiaoyaocz/dart_simple_live&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=xiaoyaocz/dart_simple_live&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=xiaoyaocz/dart_simple_live&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=xiaoyaocz/dart_simple_live&type=Date" />
 </picture>
</a>

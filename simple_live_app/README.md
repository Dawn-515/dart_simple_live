# Simple Live APP

基于Flutter开发的多平台直播观看应用，支持哔哩哔哩、斗鱼、虎牙、抖音等多个主流直播平台。

![License](https://img.shields.io/github/license/xiaoyaocz/dart_simple_live)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/xiaoyaocz/dart_simple_live)
![Platform](https://img.shields.io/badge/platform-android%20%7C%20ios%20%7C%20windows%20%7C%20macos%20%7C%20linux-blue)

## 功能特性

- 📺 **多平台支持**：支持哔哩哔哩、斗鱼、虎牙、抖音等主流直播平台
- 🖥️ **跨平台应用**：支持Android、iOS、Windows、macOS、Linux等多个平台
- 🎨 **现代化界面**：采用Material Design设计，支持深色/浅色主题切换
- 📱 **直播间功能**：
  - 高清直播视频播放
  - 实时弹幕显示与互动
  - 直播间关注与管理
  - 视频截图与分享
  - 画中画播放（Android）
- 🔍 **搜索功能**：支持按房间号或主播名搜索
- ⚙️ **个性化设置**：
  - 弹幕样式自定义
  - 播放器设置（清晰度、线路等）
  - 定时关闭功能
  - 关注列表管理
- 📚 **观看历史**：记录观看过的直播间
- ☁️ **数据同步**：支持通过WebDAV等方式同步关注列表和观看历史

## TODO

- [ ] 完善桌面平台体验
- [ ] 优化iOS播放兼容性
- [ ] 分离全屏与非全屏弹幕样式
- [ ] 重写直播间界面

## 快速开始

### 环境要求

- Flutter 3.0+
- Dart 3.0+
- Android SDK (Android开发)
- Xcode (iOS开发)
- Visual Studio (Windows开发)

### 安装依赖

```bash
flutter pub get
```

### 运行应用

```bash
# 开发模式运行
flutter run

# 指定设备运行
flutter run -d <device_id>
```

### 构建发布版本

#### Android

```bash
# 构建调试版本APK
flutter build apk --debug

# 构建发布版本APK
flutter build apk --release

# 构建AppBundle
flutter build appbundle --release
```

#### Windows

```bash
# 构建Windows应用
flutter build windows --release
```

#### macOS

```bash
# 构建macOS应用
flutter build macos --release
```

#### Linux

```bash
# 构建Linux应用
flutter build linux --release
```

## 项目结构

```
lib/
├── app/                 # 应用核心配置
│   ├── controller/      # 全局控制器
│   ├── sign/            # 平台签名算法
│   └── utils/           # 工具类
├── models/              # 数据模型
├── modules/             # 功能模块
│   ├── home/            # 首页
│   ├── live_room/       # 直播间
│   ├── mine/            # 个人中心
│   ├── follow_user/     # 关注用户
│   ├── search/          # 搜索
│   ├── settings/        # 设置
│   └── sync/            # 数据同步
├── requests/            # 网络请求
├── routes/              # 路由管理
├── services/            # 业务服务
└── widgets/             # 自定义组
```

## 技术栈

- **框架**：Flutter + GetX
- **状态管理**：GetX
- **网络请求**：Dio
- **数据存储**：Hive
- **视频播放**：MediaKit
- **弹幕系统**：Canvas Danmaku
- **UI组件**：Flutter Material Design

## 核心依赖

- `simple_live_core` - 核心直播功能库
- `media_kit` - 多媒体播放框架
- `get` - 状态管理和路由
- `hive` - 本地数据存储
- `dio` - HTTP客户端
- `canvas_danmaku` - 弹幕渲染引擎

## 使用说明

1. **首次使用**：应用启动后会自动加载各平台推荐内容
2. **搜索直播**：点击首页搜索图标，输入房间号或主播名进行搜索
3. **观看直播**：点击直播间卡片进入播放界面
4. **关注主播**：在直播间点击关注按钮，可在个人中心查看关注列表
5. **个性化设置**：在个人中心进入设置页面，调整各项参数

## 免责声明

本软件为开源软件，仅供学习交流使用：

1. 本软件完全基于个人意愿使用，使用者应对自己的使用行为承担全部责任
2. 本软件仅供学习交流、科研等非商业性质用途，严禁用于商业目的
3. 使用本软件应遵守国家相关法律法规，不得从事任何违法违规行为
4. 软件作者不对因使用本软件而产生的任何技术或安全问题承担责任

## 开源协议

本项目采用MIT License，详情请见[LICENSE](LICENSE)文件。

## 联系方式

- GitHub Issues: [https://github.com/xiaoyaocz/dart_simple_live/issues](https://github.com/xiaoyaocz/dart_simple_live/issues)
- 项目主页: [https://github.com/xiaoyaocz/dart_simple_live](https://github.com/xiaoyaocz/dart_simple_live)

## 优化建议

### 1. LiveRoomController优化建议

#### 内存泄漏风险
- 在`LiveRoomController`中使用了`WidgetsBinding.instance.addPostFrameCallback`，但没有保存回调引用，这可能导致在某些情况下无法正确清理。建议保存回调引用以便在适当时候取消。

#### 代码重复
- `LiveRoomController`中有大量重复的UI控制代码，特别是在各种设置面板的显示方法中（如`showDanmuSettingsSheet`、`showQualitySheet`等）。这些方法可以重构为更通用的方法以减少代码重复。

#### 错误处理改进
- 在`loadData`方法中，错误处理可以通过更具体的异常类型来改善用户体验。

### 2. HomeController优化建议

#### 状态管理优化
- `HomeController`中的`refreshOrScrollTop`方法可以进一步优化，避免不必要的类型转换。

### 3. FollowUserController优化建议

#### 数据一致性问题
- 在`FollowUserController`中，`setItemTag`方法中存在潜在的数据一致性问题。当更新标签时，需要确保数据库操作和内存操作保持一致。

#### 性能优化
- 在`removeTag`方法中，对于每个关注用户都执行单独的数据库更新操作，这可能会导致性能问题。可以考虑批量更新操作以提高性能。

### 4. SearchController优化建议

#### 注释代码清理
- `AppSearchController`中有一些被注释掉的代码（如抖音相关的特殊处理），这些代码应该被清理或恢复，以提高代码可读性。

### 5. 设置模块优化建议

#### UI组件复用
- 在`DanmuSettingsView`中，有很多相似的设置项，可以创建更通用的设置组件来减少代码重复。

#### 硬编码字符串
- 在字体粗细的显示值中使用了硬编码的字符串数组，这些应该提取为常量以提高维护性。

### 6. 通用优化建议

#### 内存管理
- 确保所有监听器和回调都能正确清理，防止内存泄漏。

#### 代码复用
- 减少重复代码，提高组件复用性，使代码更加简洁易维护。

#### 性能优化
- 批量处理数据库操作，避免频繁的单条更新，提高应用性能。

#### 代码清理
- 移除无用的注释代码，提高代码可读性和维护性。

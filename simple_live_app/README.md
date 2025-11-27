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
# simple_live_tv_app

基于 `simple_live_core` 实现的 Android TV Flutter 客户端，专为电视大屏优化。

## 简介

`simple_live_tv_app` 是专门为 Android TV / 电视盒子设计的直播客户端，支持遥控器操作，提供了适配大屏幕的 UI 设计和交互体验。

## 支持平台

### 直播平台

- 虎牙直播
- 斗鱼直播
- 哔哩哔哩直播
- 抖音直播

### 设备平台

- ✅ Android TV
- ✅ Android 电视盒子
- 🟡 Windows (实验性支持)

## 主要功能

### TV 专属体验

- ✅ 遥控器完美支持
- ✅ 大屏优化 UI
- ✅ D-Pad 导航
- ✅ 焦点管理优化
- ✅ Leanback 风格设计

### 直播功能

- ✅ 多平台直播间浏览
- ✅ 直播搜索
- ✅ 分类浏览
- ✅ 推荐直播
- ✅ 多清晰度选择
- ✅ 实时弹幕显示
- ✅ 弹幕设置（透明度、大小、速度等）
- ✅ 全屏播放

### 用户功能

- ✅ 关注主播
- ✅ 观看历史
- ✅ 收藏管理
- ✅ 多设备同步（二维码/局域网）

### 界面功能

- ✅ 明暗主题切换
- ✅ 自定义设置
- ✅ 网格布局

## 环境要求

- Flutter SDK: `>=3.1.2 <4.0.0`
- Dart SDK: `>=3.1.2`
- Android TV / 电视盒子 (Android 5.0+)

## 快速开始

### 1. 安装依赖

```bash
cd simple_live_tv_app
flutter pub get
```

### 2. 运行项目

```bash
# Android TV
flutter run

# Windows (实验性)
flutter run -d windows
```

### 3. 构建发布版

```bash
# Android TV APK
flutter build apk --release

# Android TV App Bundle
flutter build appbundle --release
```

## 项目结构

```
lib/
├── app/              # 应用程序核心
├── models/          # 数据模型
├── modules/         # 功能模块
│   ├── areas/        # 分区
│   ├── category/     # 分类
│   ├── favorites/    # 收藏
│   ├── home/         # 首页
│   ├── live_room/    # 直播间
│   ├── other/        # 其他
│   ├── popular/      # 热门
│   ├── search/       # 搜索
│   ├── settings/     # 设置
│   └── sync/         # 同步
├── requests/        # 网络请求
├── routes/          # 路由配置
├── services/        # 服务层
├── widgets/         # 公共组件
└── main.dart        # 入口文件
```

## 主要依赖

- **框架**: GetX (状态管理 + 路由)
- **网络**: Dio
- **数据库**: Hive
- **视频播放**: Media Kit
- **弹幕**: Canvas Danmaku
- **UI 适配**: Flutter ScreenUtil

## TV 交互说明

### 遥控器按键映射

- **方向键**: 导航、移动焦点
- **确认键**: 选择/播放
- **返回键**: 返回上一级
- **菜单键**: 打开设置
- **播放/暂停**: 控制播放

### 焦点系统

应用使用了 Flutter 的 Focus 系统，保证遥控器操作的流畅性。所有可交互元素都经过遥控器优化。

## 同步功能

### 二维码扫码同步

1. 在 TV 端打开同步设置
2. 生成二维码
3. 使用手机 APP 扫码
4. 完成数据同步

### 局域网同步

当手机和 TV 在同一局域网时，可以通过 UDP 发现和 SignalR 进行实时同步。

## 开发说明

### 代码生成

项目使用 Hive 数据库，修改模型后需要重新生成代码：

```bash
flutter packages pub run build_runner build
```

### TV 调试

建议使用 Android Studio 的 Android TV 模拟器进行开发和调试，或者使用真实的 Android TV / 电视盒子设备。

### UI 适配

项目使用 `flutter_screenutil` 进行屏幕适配，基准分辨率为 1920x1080。

## 注意事项

- 建议使用 Android 7.0 及以上版本获得最佳体验
- 部分电视盒子可能需要允许安装未知来源应用
- 推荐使用有线网络连接以获得更好的播放体验
- 本应用目前处于 BETA 阶段，可能存在一些问题

## 常见问题

### 无法识别遥控器

- 确认设备支持 Android TV 模式
- 检查遥控器电池和配对状态

### 播放卡顿

- 检查网络连接
- 尝试降低清晰度
- 关闭弹幕功能

### 同步无法连接

- 确保手机和 TV 在同一局域网
- 检查防火墙设置
- 尝试重启APP

## 许可证

本项目仅用于学习交流，严禁用于商业目的。


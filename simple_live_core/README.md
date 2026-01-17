# simple_live_core

项目核心库，实现获取各个直播平台的信息及弹幕。

## 简介

`simple_live_core` 是一个跨平台的 Dart 聚合直播核心库，提供了统一的接口来获取多个直播平台的数据，包括直播间信息、分类、搜索、播放链接和实时弹幕等。

## 支持的平台

- **虎牙直播** (HuyaSite)
- **斗鱼直播** (DouyuSite)
- **哔哩哔哩直播** (BiliBiliSite)
- **抖音直播** (DouyinSite)

## 主要功能

### 直播站点操作

- ✅ 获取平台分类列表
- ✅ 搜索直播间/主播
- ✅ 获取分类下的直播间列表
- ✅ 获取推荐直播间
- ✅ 获取直播间详细信息
- ✅ 获取直播清晰度列表
- ✅ 获取播放链接
- ✅ 查询直播状态
- ✅ 获取 SuperChat 消息（B站）

### 弹幕功能

- ✅ 实时接收弹幕消息
- ✅ 接收礼物消息
- ✅ 接收SC/醒目留言
- ✅ 接收在线人气值

## 快速开始

### 安装

在 `pubspec.yaml` 中添加依赖：

```yaml
dependencies:
  simple_live_core:
    path: ../simple_live_core  # 本地路径
```

### 基本使用

```dart
import 'package:simple_live_core/simple_live_core.dart';

void main() async {
  // 创建直播站点实例
  var site = BiliBiliSite();
  
  // 获取直播间详情
  var detail = await site.getRoomDetail(roomId: '23058');
  print('房间标题: ${detail.title}');
  print('主播: ${detail.userName}');
  print('在线人数: ${detail.online}');
  
  // 获取播放清晰度
  var qualities = await site.getPlayQualites(detail: detail);
  
  // 获取播放链接
  if (qualities.isNotEmpty) {
    var playUrl = await site.getPlayUrls(
      detail: detail,
      quality: qualities.first,
    );
    print('播放链接: ${playUrl.urls.first}');
  }
  
  // 接收弹幕
  var danmaku = site.getDanmaku();
  danmaku.onMessage = (LiveMessage msg) {
    if (msg.type == LiveMessageType.chat) {
      print('${msg.userName}: ${msg.message}');
    }
  };
  await danmaku.start(detail.danmakuData);
}
```

## 核心接口

### LiveSite

所有直播平台的基类，定义了统一的接口：

```dart
class LiveSite {
  String id;                    // 站点唯一ID
  String name;                  // 站点名称
  
  Future<List<LiveCategory>> getCategores();                           // 获取分类
  Future<LiveSearchRoomResult> searchRooms(String keyword);           // 搜索直播间
  Future<LiveSearchAnchorResult> searchAnchors(String keyword);       // 搜索主播
  Future<LiveCategoryResult> getCategoryRooms(LiveSubCategory category); // 获取分类房间
  Future<LiveCategoryResult> getRecommendRooms();                     // 获取推荐
  Future<LiveRoomDetail> getRoomDetail({required String roomId});     // 获取房间详情
  Future<List<LivePlayQuality>> getPlayQualites({required LiveRoomDetail detail}); // 获取清晰度
  Future<LivePlayUrl> getPlayUrls({required LiveRoomDetail detail, required LivePlayQuality quality}); // 获取播放链接
  Future<bool> getLiveStatus({required String roomId});               // 查询直播状态
  LiveDanmaku getDanmaku();                                           // 获取弹幕实例
}
```

### LiveDanmaku

弹幕接收基类：

```dart
class LiveDanmaku {
  Function(LiveMessage msg)? onMessage;  // 消息回调
  Function(String msg)? onClose;         // 关闭回调
  
  Future start(dynamic args);            // 启动弹幕连接
  Future stop();                         // 停止弹幕连接
}
```

## 数据模型

- **LiveCategory**: 直播分类
- **LiveRoomItem**: 直播间简要信息
- **LiveRoomDetail**: 直播间详细信息
- **LivePlayQuality**: 播放清晰度
- **LivePlayUrl**: 播放链接
- **LiveMessage**: 弹幕消息
- **LiveAnchorItem**: 主播信息

## 依赖项

- `dio`: HTTP 网络请求
- `web_socket_channel`: WebSocket 连接
- `protobuf`: Protocol Buffers 支持
- `crypto`: 加密算法
- `brotli`: Brotli 压缩
- `dart_quickjs`: JavaScript 执行引擎
- `tars_dart`: TARS 协议支持

## 开发

### 运行测试

```bash
dart test
```

### 示例程序

查看 `example/simple_live_core_example.dart` 获取更多使用示例。

## 许可证

本项目仅用于学习交流，严禁用于商业目的。

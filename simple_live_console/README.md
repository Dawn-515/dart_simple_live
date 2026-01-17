# simple_live_console

基于 `simple_live_core` 的命令行控制台程序，用于快速获取直播间信息、播放链接和实时弹幕。

## 简介

`simple_live_console` 是一个轻量级的命令行工具，无需 GUI 界面即可快速获取直播间的各种信息。适合用于：

- 快速获取直播播放链接
- 监控直播间弹幕
- 自动化脚本集成
- 服务器环境调试

## 支持的平台

- 虎牙直播 (huya.com)
- 斗鱼直播 (douyu.com)
- 哔哩哔哩直播 (bilibili.com)
- 抖音直播 (live.douyin.com)

## 安装与构建

### 前置要求

- Dart SDK >= 3.10.0

### 构建可执行文件

```bash
# 进入项目目录
cd simple_live_console

# 获取依赖
dart pub get

# 编译成可执行文件
dart compile exe bin/simple_live_console.dart -o simple_live.exe
```

## 使用方法

### 获取直播间信息和播放链接

输入直播间链接获取房间信息及播放地址：

```bash
simple_live.exe -i [URL]
```

**示例**：

```bash
# B站
simple_live.exe -i https://live.bilibili.com/23058

# 虎牙
simple_live.exe -i https://www.huya.com/660000

# 斗鱼
simple_live.exe -i https://www.douyu.com/96291

# 抖音
simple_live.exe -i https://live.douyin.com/123456789
```

**输出示例**：

```
来源：哔哩哔哩直播
房间号：23058
房间标题：某某直播间
直播用户：主播名称
人气值：12345
状态：直播中
可用清晰度：
【１】原画
【２】蓝光
【３】超清
请输入【】内数字，获取对应清晰度的直链
```

然后输入数字选择清晰度，程序会输出对应的播放链接。

### 获取直播间弹幕

输入直播间链接持续输出实时弹幕：

```bash
simple_live.exe -d [URL]
```

**示例**：

```bash
simple_live.exe -d https://live.bilibili.com/23058
```

**输出示例**：

```
来源：哔哩哔哩直播
房间号：23058
房间标题：某某直播间
直播用户：主播名称
状态：直播中
【开始获取弹幕】
-----人气值：12345-----
用户A：666
用户B：主播加油！
-----人气值：12350-----
...
```

按 `Ctrl+C` 停止接收弹幕。

### 查看帮助

```bash
simple_live.exe -h
```

## 命令参数

| 参数 | 说明 |
|------|------|
| `-i [URL]` | 获取直播间信息及播放直链 |
| `-d [URL]` | 持续输出直播间弹幕 |
| `-h` | 显示帮助信息 |

## 使用场景

### 1. 配合播放器使用

```bash
# 获取播放链接后使用 mpv 播放
simple_live.exe -i https://live.bilibili.com/23058
# 复制输出的 URL
mpv <copied_url>
```

### 2. 弹幕监控

```bash
# 监控直播间弹幕，将输出保存到文件
simple_live.exe -d https://live.bilibili.com/23058 > danmaku.log
```

### 3. 脚本集成

可以将命令集成到自动化脚本中，实现自动化直播监控、数据采集等功能。

## 开发

### 直接运行（不编译）

```bash
dart run bin/simple_live_console.dart -i [URL]
```

### 运行测试

```bash
dart test
```

## 注意事项

- 请确保网络连接正常
- 直播间链接必须是完整的 URL
- 部分平台可能有限流或防爬措施，如遇到问题请稍后重试

## 依赖

- `simple_live_core`: 直播核心库

## 许可证

本项目仅用于学习交流，严禁用于商业目的。
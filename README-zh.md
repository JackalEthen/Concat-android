<div align="center">

<table width="100%">
  <tr>
    <td align="left" width="120">
      <img src="https://cdn.jsdelivr.net/gh/jub0t/Concat@main/assets/logo-dark.png" alt="Concat" width="100" />
    </td>
    <td align="right">
      <h1>Concat 安卓版</h1>
      <h3 style="margin-top: -10px;">真正自由开源的视频编辑器，为掌心重构。</h3>
    </td>
  </tr>
</table>

<p>
  <b>简体中文</b> ·
  <a href="README.md">English</a>
</p>

<p>
  <img src="https://img.shields.io/badge/平台-Android%20arm64-c6f432?style=flat&logo=android&logoColor=F8F8F8&labelColor=000000" alt="平台：Android arm64" />
  <img src="https://img.shields.io/badge/界面-紧凑模式-c6f432?style=flat&labelColor=000000" alt="界面：紧凑模式" />
  <img src="https://img.shields.io/badge/语言-14%20种-c6f432?style=flat&labelColor=000000" alt="语言：14 种" />
  <img src="https://img.shields.io/badge/许可-AGPL%20v3-c6f432?style=flat&logo=gnu&logoColor=F8F8F8&labelColor=000000" alt="许可：AGPL v3" />
</p>

</div>

---

## 关于

这里是 [Concat](https://github.com/jub0t/Concat) 的安卓版主页——真正自由开源的跨平台剪映替代品。桌面引擎一行未动；这个分支增加的是**手机优先的紧凑界面**，以及让视频编辑器真正能单手使用的安卓专项工程。

手机屏幕不是缩小版的桌面。把时间线编辑器硬塞进竖屏窗口，每个按钮都会小到指尖点不中。所以紧凑模式没有缩放桌面布局，而是为 Concat **从手机出发重新设计了一套布局**——引擎相同、工程文件相同，但界面按拇指的规律工作。

无水印、无付费墙、无账号、100% 本地运行。

## 紧凑模式

窗口宽度小于 860 像素——也就是所有手机——自动切换到紧凑布局。旋转或拉宽窗口，桌面布局原样恢复。

<table>
<tr><td width="50%">

### 🎛️ 双行播放控制

播放、分割和时间码位于固定的双行栏中，触控目标宽大，用弹性间隔居中。不用捏着屏幕去够播放键。

</td><td width="50%">

### 🎚️ 装进手掌的轨道头

每条轨道一个固定 44 像素的头部列，承载锁定 / 显示 / 静音开关。长按打开遮罩浮层执行删除——不用翻找隐藏菜单。

</td></tr>
<tr><td>

### 📑 面板抽屉

编辑区最多容纳两个面板，其余全部停靠在抽屉里。点停靠行的 ↑/↓ 换入席位，被替换的面板自动归位。最后一个席位不可关闭。

</td><td>

### 🍔 图标标题栏

汉堡菜单替代三个文字菜单，工程名内联显示，点击 logo 打开抽屉。没有窗口按钮——安卓自带。

</td></tr>
<tr><td>

### 👆 不冲突的手势

即使子控件处理自己的手势，纵向滑动仍然滚动面板堆栈。

</td><td>

### 🧭 两级设置

设置改为两级导航，不再是一页到底；弹窗被限制在窗口内。

</td></tr>
</table>

## 安卓专项工程

除了布局，这个分支还修好了只在手机上出现的问题：

- **中文在任何 ROM 上都能显示。** 部分 ROM（华为、OPPO）的字体配置无法被第三方字体栈匹配——汉字显示为方框而日语正常。Concat 现在内置 *Noto Sans CJK*（SIL OFL 许可），在字体集合构建之前完成加载，并挂到每种文字的回退链上。全部 14 种界面语言在任何 ROM 上正确渲染。
- **原生文档选择。** 通过编译进 APK 的小型 Java 片段调用系统文件选择器——选中的文件复制进应用存储，按路径交给编辑器。
- **日志不依赖数据线。** 窗口输出的所有内容同时写入 `logcat`（tag `concat`）*和* 设置里能打开的日志文件——因为拿在手里的手机没有线。
- **硬件解码自主可选。** 硬解开关就在设置里。

## 自己动手构建

你需要 Android SDK + NDK、Rust 的 `aarch64-linux-android` target，第一次大约一小时。

```bash
cd src
cargo apk build -p concat-android --target aarch64-linux-android
adb install target/debug/apk/Concat.apk
```

FFmpeg 与引擎从源码交叉编译（`src/scripts/`）；sherpa-onnx 与 Skia 使用预编译包。

## 致谢与许可

- **上游项目**：[jub0t/Concat](https://github.com/jub0t/Concat) —— 桌面引擎，这个分支存在的理由。
- **字体**：Google 出品的 [Noto Sans CJK](https://fonts.google.com/noto)，SIL 开放字体许可。
- 采用与上游一致的 **AGPL-3.0-or-later** 许可。欢迎贡献。

---

<div align="center">
<sub>无水印 · 无付费墙 · 无账号 · 100% 本地运行</sub>
</div>

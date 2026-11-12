# 浮岛 FloatIsle 开发指南

- 用中文与项目负责人沟通。
- 本仓库包含基础宿主、共用界面与框架、沙滩、草地和粉色森林三个免费主题；其他主题只保留带锁的名称、简介和缩略图，不包含页面、参数、脚本或其他实现代码。
- 界面只保留简体中文和英文，不跟随主程序增加其他语言。
- 不提供账号登录、购买或自动检查更新功能，不接入授权服务、官网更新清单或商店更新接口。锁定主题点开只显示“即将推出”。
- 保持 `themes.json`、主题参数默认值和中英文文案一致；锁定主题没有 `page` 和 `groups`，点击只打开“即将推出”说明，不能切换当前壁纸。
- 修改主题后检查图标移动、预览、暂停和分享；所有画布按实际像素与小数显示尺寸绘制。
- 壁纸常驻后台，以核显 30fps 为目标。静态绘图进入缓存，小物体使用局部图层，不在全屏着色器中逐个计算大量物体。
- `prototype/thumbs/` 是人工设计的缩略图，未经要求不要重新生成或覆盖。`prototype/thumbs/pink-forest.webp` 是粉色森林主题的缩略图（复制自原锁定主题的同名缩略图）。
- 主程序：`powershell -ExecutionPolicy Bypass -File host\build.ps1`；产物 `host/bin/FloatIsle.exe`。
- 浏览器预览：`node prototype\serve.mjs`，访问 `http://localhost:5178/settings.html`。
- Windows 宿主：`host/DesktopHost.cs`；改主题 HTML/JS 不需要重新编译宿主，托盘“重新载入”即可。
- 产品显示名为 `浮岛 FloatIsle`；程序读写 `%LOCALAPPDATA%\FloatIsle`，安装到 `Programs\浮岛 FloatIsle`，启动项和运行实例标识也与原版分开，不要改回共用身份。
- 不提交 `host/bin/`、`host/lib/`、个人数据、凭证或本机路径。
- 许可见 `LICENSE`，名称和图标的说明见 `TRADEMARKS.md`。
- 上游历史（Deskland Preview）：2026-11-06 发布 GitHub Release `v0.1.2`，包含 Windows x64 安装包、对应源码 ZIP、SHA256 和文件清单；2026-11-07 发布 `v0.1.3`，同步启动与缩略图修复。安装包未签名。
- 2026-11-12：改名重做为浮岛 FloatIsle v0.1.0。基于 Deskland Preview v0.1.3（HEAD 9818b57）修改：全仓库改名（Deskland → 浮岛 FloatIsle，含托盘、互斥体、Run 键名、数据目录、安装包名），删掉旧名 HabitatWallpaper 的迁移代码（上游遗留的死代码，从未被调用）；新增粉色森林主题（复用草地引擎，粉白 + 薄荷绿配色，树画在 2D 叠加层上）；新增 `.github/workflows/build-windows.yml`（windows-latest 云端构建安装包）。`themes.json` 现为 13 个主题：可用 3 个（beach、meadow、pink-forest），锁定 10 个。沙箱 Linux 打不出 Windows 安装包，Windows 构建与图标读取尚未实测。

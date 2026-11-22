# 抖音图文提取器 · 使用指南

`douyin-image-extractor` 的配套说明仓库：功能概览、安装与使用步骤、常见问题和版本索引。代码、发布包和技术细节都在主仓库，这里只做索引，避免两处描述不一致。

- 主仓库：https://github.com/adigailmichael19-art/douyin-image-extractor
- Android APK：https://github.com/adigailmichael19-art/douyin-image-extractor/releases/tag/android-debug
- 更新记录：https://github.com/adigailmichael19-art/douyin-image-extractor/blob/main/CHANGELOG.md

## 它是什么

Windows 桌面程序（Python + Tkinter）与原生 Android 应用（Java），用于保存**公开可访问**的抖音图文作品：原图、文案、作者信息和可选 MP4 视频；图片下载完整后可自动按顺序合成 PDF，并导出到系统相册。

> 仅供个人学习与技术研究。请遵守平台规则与适用法律，尊重原创作者版权，不要将下载内容用于未经授权的传播或商业用途。

## 环境与安装

| 平台 | 要求 | 获取方式 |
| --- | --- | --- |
| Windows | Windows 10/11，Python 3.12+ | 克隆主仓库后执行 `python -m pip install -r requirements.txt` |
| Android | Android 7.0（API 24）及以上 | 从 Release 下载 `app-debug.apk`（debug 签名，仅供测试） |

Windows 启动：

```powershell
python src/douyin_gui.py
```

也可以双击 `launch.vbs` 静默启动，启动器里只需把 `PYTHON_EXE` 改成你本机的 Python 路径。

## 使用步骤

1. 在抖音里复制作品链接或整段分享口令（短链、完整链接、App 口令都支持）
2. 桌面版粘贴到链接框，每行一个，可批量；选择输出目录
3. 需要时勾选“视频作品自动下载 mp4”，点“开始提取”
4. 每个作品输出到独立目录，包含图片或视频、`info.json`、`caption.txt`
5. 图文作品的图片全部下载成功后，自动生成同名 PDF，并导出到系统相册（Android：`Pictures/DouyinExtractor`）

## 常见问题

**Q：提示“无法获取作品数据”怎么办？**
作品页可能只返回了风控空壳。先确认链接能在浏览器里正常打开；仍失败时，在“Cookie（可选）”里填本人浏览器中的 Cookie 重试。应用会先自动申请匿名访客 Cookie，不使用账号登录。

**Q：支持视频吗？**
支持。视频作品会保存 MP4；图文作品本身没有视频文件，只保存图片。

**Q：会自动合成 PDF 吗？**
会。图文作品图片全部下载成功时，按原始顺序合成一个 PDF，每个作品一个文件；图片不全、任务被停止或失败时不生成。

**Q：图片数量比页面上少？**
页面可能只下发了部分候选地址，或个别候选被拦截。日志会写明成功数量与保存目录，可换 Cookie 重试。

**Q：会绕过登录、付费或验证码吗？**
不会。命中验证环境时直接记录并停止该路径，不点击也不破解任何验证控件。

**Q：能商用或批量搬运别人的作品吗？**
不建议也不被支持，请只保存你有权使用的内容。

## 版本与更新

版本记录见主仓库 [CHANGELOG.md](https://github.com/adigailmichael19-art/douyin-image-extractor/blob/main/CHANGELOG.md)。Android 当前为 `1.7`（versionCode 8），由 CI 自动构建并发布到 `android-debug` 预发布版本。

## 反馈

- 使用问题：主仓库 [Issues](https://github.com/adigailmichael19-art/douyin-image-extractor/issues)，请先搜索，日志里去掉 Cookie 与个人信息
- 安全问题：按 [SECURITY.md](https://github.com/adigailmichael19-art/douyin-image-extractor/blob/main/SECURITY.md) 走私密报告

## 本仓库的定位

只做面向使用者的说明与索引，不放代码副本，也不重复主仓库的技术细节。两边不一致时，以主仓库为准。

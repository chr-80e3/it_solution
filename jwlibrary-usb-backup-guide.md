# 手动备份 JW Library 数据到 USB 随身碟

JW Library 的数据通常存储在以下路径：

`C:\Users\[你的用户名]\AppData\Local\Packages\WatchtowerLibrary.[随机字符串]\LocalState`

---

## ✅ 备份步骤

1. 打开文件资源管理器，启用“显示隐藏文件”。
2. 导航到上述路径。
3. 将整个 `LocalState` 文件夹复制到你的 USB 随身碟中。

> ⚠️ 注意：该路径中的文件包含已下载的出版物、音频、视频和笔记等数据。

---

## 🔄 恢复备份到新设备或新安装

1. 在新设备上安装 JW Library。
2. 关闭 JW Library 应用。
3. 将 USB 中的 `LocalState` 文件夹复制回相同路径，覆盖新安装的空文件夹。
4. 重新打开 JW Library，它将识别已下载的内容。

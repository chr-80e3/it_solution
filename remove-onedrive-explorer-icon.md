## 如何隐藏 OneDrive 图标（通过注册表修改）

### 1. 打开注册表编辑器
- 按下 `Win + R` 键打开“运行”对话框。
- 输入 `regedit` 并按 `Enter` 键。

### 2. 找到 OneDrive 的 CLSID
- 在注册表编辑器中，导航到以下路径：`HKEY_CLASSES_ROOT\CLSID`

### 3. 查找并修改 OneDrive 条目
- 在 `CLSID` 下，使用 `Ctrl + F` 搜索 `OneDrive`。
- 点击“查找下一个”直到找到与 OneDrive 相关的条目。
- 找到该条目后，右键修改选定的项。（例如：`System.IsPinnedToNameSpaceTree`）
- 将“数值数据”修改为 `0`。

### 4. 重启 Windows 资源管理器
- 按 `Ctrl + Alt + Del`，选择“任务管理器”。
- 在“进程”选项卡下，找到并右键单击“Windows 资源管理器”。
- 选择“重启”。

> ✅ 完成以上步骤后，OneDrive 图标将从文件资源管理器中消失。

# OpenWRT DAED 编译配置准备

本文档介绍如何通过 `menuconfig` 配置 OpenWRT，以启用内核调试功能、BPF 支持和 `daed` 功能模块。

---

## 配置步骤

### 1. 进入 `menuconfig` 界面
在项目根目录下，运行以下命令：
```bash
make menuconfig
```

### 2. 配置内核构建选项
1. 在菜单中导航到：
   ```
   Global build settings → Kernel build options
   ```
2. 进行以下设置：
   - **取消勾选** `Reduce debugging information`  
   - **选中** `Enable additional BTF type information`  
   - **选中** `Compile the kernel with BPF event support`  
   - **选中** `XDP sockets support`  

### 3. 返回主菜单
按 `Esc` 键两次，或选择 `Exit`，直到返回 `menuconfig` 主菜单。

### 4. 配置高级选项
1. 在主菜单中导航到：
   ```
   Advanced configuration options (for developers)
   ```
   然后进入该选项。
2. 进入以下子菜单：
   ```
   BPF toolchain (Use host LLVM toolchain)
   ```
3. 进行以下设置：
   - **选中** `Use host LLVM toolchain`  

### 5. 保存并退出
按 `Esc` 返回主界面，选择 `Save` 保存配置并退出。

### 6. 验证配置
1. 编译完成后，将生成的固件刷入设备。
2. 进入设备的 LuCI 界面，确认 `daed` 功能已启用。

---

## 注意事项
- 请确保已正确安装支持 LLVM 的工具链。
- 编译完成后，建议检查日志确保配置正确生效。

---

如果有任何问题，欢迎提交 Issue 或 Pull Request。

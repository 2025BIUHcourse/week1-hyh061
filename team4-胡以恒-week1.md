# Week1 实验报告
## 1. 实验任务
1. 完成 Windows 11 + Ubuntu 20.04 双系统安装与启动切换
2. 安装 VSCode 并配置 C++ 环境，成功运行helloworld
3. 学习 Git 基础命令，创建符合格式的 GitHub 账号并加入小组，提交本周作业。
4. 按规范编写 Markdown 实验报告，包含过程说明、实验截图、问题记录与模块理解。


## 2. 实现过程（含主要步骤与截图）
### 2.1 双系统安装（Windows 11 + Ubuntu 20.04）
1. **前期准备**：下载 Ubuntu 20.04 镜像文件，用工具将镜像写入 U 盘（选择 UEFI 启动模式）；在 Windows 11 中通过“磁盘管理”压缩出未分配空间，用于安装 Ubuntu。
2. **BIOS 设置**：重启电脑并按快捷键F2进入 BIOS，开启 UEFI 启动模式，关闭 Secure Boot，将 U 盘设为第一启动项。
3. **Ubuntu 安装与分区**：从 U 盘启动进入 Ubuntu 安装界面，选择“安装 Ubuntu”，在分区步骤选择“其他选项”，手动划分 3 个分区：
   - EFI 分区：大小 500MB，类型选“EFI 系统分区”。
   - SWAP 分区：大小 1000MB,类型选“交换空间”。
   - EXT4 分区：剩余未分配空间，挂载点设为“/”，类型选“EXT4 日志文件系统”。
4. **完成安装与启动切换**：设置用户名和密码后等待安装完成，重启电脑会自动显示 GRUB 启动菜单，可选择进入 Windows 11 或 Ubuntu 20.04。

### 2.2 VSCode 安装与 C++ 环境配置
1. **安装 VSCode**：打开 Ubuntu 终端，执行命令`sudo apt update`更新软件源，再执行`sudo apt install code`安装 VSCode；安装完成后从应用列表启动 VSCode。
2. **安装 C++ 相关扩展**：在 VSCode 左侧“扩展”面板，搜索并安装“C/C++”（Microsoft 官方插件）、“Code Runner”（快速运行代码）。
3. **运行 Hello World 程序**：
   - 创建`hello.c`文件，写入代码：
     ```c
    #include <stdio.h>
    int main() {
        printf("Hello World\n");
    }

     ```
   - 点击右上角“运行代码”按钮（或右键选择“Run Code”），底部终端显示“Hello World!”，确认程序运行成功。

### 2.3 Git 学习与作业上传
1. **创建 GitHub 账号**：访问 GitHub 官网，注册账号，用户名格式设为“张三_2025001”（姓名+学号），完成邮箱验证后登录。
2. **加入 GitHub 小组**：点击任务要求中的“第 X 组”链接（如第 3 组），申请加入小组仓库，等待管理员通过。
3. **Git 配置与命令操作**：
   - 打开 Ubuntu 终端，执行命令安装 Git：`sudo apt install git`。
   - 配置全局用户信息：
     ```bash
     git config --global user.name "张三_2025001"
     git config --global user.email "zhangsan@example.com"
     ```
   - 新建本地作业文件夹`week1-homework`，进入文件夹后初始化仓库：`git init`。
   - 将实验报告（.md 文件）、截图等材料放入该文件夹，执行`git add .`将所有文件加入暂存区。
   - 提交暂存区文件：`git commit -m "week1 submit"`。
   - 关联远程仓库：`git remote add origin https://github.com/xxx/xxx.git`（替换为小组仓库链接）。
   - 重命名分支为 main：`git branch -M main`。
   - 推送文件到远程仓库：`git push -u origin main`，输入 GitHub 账号密码（或令牌）完成提交。

### 2.4 Markdown 实验报告编写
1. 在 VSCode 中新建文件，命名为“team_张三_week1_final.md”，按任务要求的报告格式，使用 Markdown 语法编写内容：
   - 用`#` `##`表示标题层级，`**内容**`表示粗体，`| 列1 | 列2 |`表示表格。
   - 插入截图时使用语法`![截图说明](截图路径)`（截图保存在与报告同级的“images”文件夹中）。
   - 代码块用```包裹，指定语言类型（如```bash ```cpp）。
2. 按快捷键 Ctrl+Shift+V 打开预览窗口，实时调整格式，确保内容清晰、符合规范。


## 3. 遇到的问题与解决方法
### 3.2 VSCode 运行 C++ 程序时提示“没有找到 g++”
- **问题原因**：未安装 C++ 编译器（build-essential 包）。
- **解决过程**：1. 打开终端，执行`sudo apt install build-essential`安装 g++、gcc 等工具；2. 重启 VSCode，重新运行 Hello World 程序，成功输出结果。

## 4. 总结与心得
通过本周实验，我系统掌握了双系统安装、VSCode 配置、Git 基础操作和 Markdown 报告编写四大核心技能。在双系统安装中，理解了 UEFI 启动模式与分区的关键作用；VSCode 扩展与 C++ 环境的配置，让我熟悉了 Linux 下的编程工具使用流程；Git 命令的实践（init/add/commit/push）则清晰展现了“本地仓库-暂存区-远程仓库”的代码管理逻辑，也解决了 GitHub 令牌登录的常见问题。

此外，Markdown 语法的应用让实验报告更规范、易读，截图与文字结合能更直观地呈现实验过程。后续需要进一步熟练 Git 分支管理、VSCode 调试功能，为后续课程的代码开发与协作打下基础。
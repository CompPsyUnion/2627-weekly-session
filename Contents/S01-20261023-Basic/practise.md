## VSCode 相关操作

```bash

Ctrl + Shift + P    # 打开命令面板

Ctrl + P            # 快速打开文件

Ctrl + W            # 关闭当前标签

Ctrl + Shift + T    # 重新打开刚才关闭的标签

Ctrl + Shift + N    # 新建独立窗口

Ctrl + S            # 保存（重要性不必多言）

Ctrl + ,            # 打开设置

# 编辑技巧

Alt + Click         # 在任意位置手动添加光标

Ctrl + Alt + 上/下  # 在当前行的上方或者下方添加光标

Ctrl + D            # 逐个选中相同的词

Ctrl + C            # 直接复制整行（不是选中复制，不要小看了）

Ctrl + X            # 直接剪切整行

Ctrl + Shift + K    # 删除整行

# 导航搜索

F12                 # 跳转到定义（你猜什么意思？试试就知道了，选中一个python中的函数然后按下F12）

Ctrl + Shift + F    # 全局搜索

Ctrl + F            # 当前文本内搜索

F2                  # 批量重命名

```

---

## VSCode 实用插件

- Prettier

```js
//Origin version

const user={name:'Alice',age:25,hobbies:['reading','coding','hiking']};
function greet(user){if(user.age>=18){console.log(`Hello, ${user.name}! You are an adult.`)}else{console.log(`Hi, ${user.name}!`)}}

//Prettier version:

const user = {
  name: "Alice",
  age: 25,
  hobbies: ["reading", "coding", "hiking"],
};

function greet(user) {
  if (user.age >= 18) {
    console.log(`Hello, ${user.name}! You are an adult.`);
  } else {
    console.log(`Hi, ${user.name}!`);
  }
}
```

- Error Lens

- Code Spell checker

---

## 可执行文件

什么是可执行文件：包含机器码、可由操作系统直接加载并运行的二进制程序文件。

对于 Windows（通过文件后缀名识别）：

- 后缀为 `.exe` 的文件（像 `.bat` 批处理脚本本质上是纯文本，双击时其实是由系统的 `cmd.exe` 去读取并执行里面的命令）

对于 macOS / Linux（通过文件的「可执行权限」识别，不依赖后缀名）：

- 命令行程序与编译产物通常为**无后缀文件**（如编译生成的 `test`）

- 桌面软件通常打包为 `.app`（应用包，本质是一个文件夹，内部存放着真正的无后缀二进制可执行文件）

---

## 快捷方式

什么是快捷方式：一个只记录了目标文件路径的“路标”文件（Windows 下后缀为 `.lnk`，图标左下角带小箭头），本身只有几 KB，**不包含程序本体**。

- 注意：删除快捷方式不会卸载原程序；把程序发给别人时，只发快捷方式是无法运行的。

尝试对心仪的可执行文件使用 ~~炎拳~~ 创建快捷方式吧：

- Windows：右键点击文件选择 **"创建快捷方式"**（Win11 需先点“显示更多选项”），或者**按住 `Alt` 键直接拖拽文件**。

- macOS：右键点击文件选择 **"制作替身"**（Make Alias），或者**按住 `Option + Command` 键直接拖拽文件**。

---

## 截图

---

## 编译实践

准备测试文件 `test.c` 和 `test.py`：

```c
// test.c
#include "stdio.h"
#include "stdlib.h"

int main()
{
    printf("hello world\n");
    system("pause");
    return 0;
}
```

```python
# test.py
print("Hello world")
```

C 语言编译的四个阶段（每一步完成后可以在 VSCode 中打开生成的文件观察变化）：

```bash
# 1. 预处理：展开头文件、宏替换、去掉注释（生成文本文件 test.i，查看文件末尾）
gcc -E test.c -o test.i

# 2. 编译：将预处理代码翻译为汇编代码（生成文本文件 test.s）
gcc -S test.i -o test.s

# 3. 汇编：将汇编代码转为二进制机器码（生成目标文件 test.o，此时已变为二进制）
gcc -c test.s -o test.o

# 4. 链接：将目标文件与系统库链接，生成最终可执行文件
gcc test.o -o test
```

Python（解释型）和 C（编译型）对比：

```bash
# C 语言：一步编译生成可执行文件，再运行该文件
gcc test.c -o test
./test          # macOS / Linux
.\test.exe      # Windows

# Python：无需手动编译生成可执行文件，直接由解释器读取运行
python test.py
```

- 编译型语言（如 C）：先将源码整体翻译成机器码可执行文件再运行，执行效率高。

- 解释型语言（如 Python）：不生成独立的机器码可执行文件，依赖解释器执行，跨平台与开发便捷，但运行开销较大。

---

## 计算机基础元器件

冯·诺依曼体系五大部件：

- CPU：含 1. 控制器 + 2. 运算器

- 3. 存储器（主存，硬盘）

- IO设备：含 4. 输入设备（键盘、鼠标等）+ 5. 输出设备（显示器、音响等）

  - USB Type-B / Type-C 等接口标准

其他重要组件：

- GPU（图形/并行协处理器，不属于经典五大部件）

- 主板

- 网卡

- 总线

---

CPU：

- 计算机的核心，内部包含控制器（CU）和运算器（ALU）

- 控制器负责指令译码与调度

- 运算器负责算术运算和逻辑运算

- 多核（现代 CPU 集成多个核心，可同时处理多个任务）

---

GPU：

- 专用的并行处理器，擅长大规模数值计算和图形渲染

- 极大的数据吞吐量

- 并行运算非常快（核心数远多于 CPU，但单核能力弱于 CPU）

- 显存（独立显卡自带专用高速显存；集成显卡/核显则与 CPU 共享主存）

---

存储：

存储结构：

| 层级 | 典型介质 | 访问时间量级 | 容量量级 | 易失性 |
| --- | --- | --- | --- | --- |
| 寄存器 | 触发器（CPU 芯片内） | 亚纳秒 ~ 1 周期 | 几十 ~ 几百字节 | 易失 |
| Cache | SRAM | 0.5 ~ 20 ns（L1 ~ L3） | KB ~ 几十 MB | 易失 |
| 主存 | DRAM | 50 ~ 70 ns | GB ~ TB | 易失 |
| 辅存 | HDD / SSD | 毫秒级（HDD）/ 微秒级（SSD） | TB ~ PB | **非易失** |

---

主板：

- 整体的骨架，所有部件都安装在主板上或通过主板连接

- 承载芯片组、扩展插槽，统筹兼顾通信和供电

---

网卡：

- 有线网卡（通过网线连接，速率稳定）

- 无线网卡（通过 Wi-Fi 连接）

- 虚拟网卡（由软件模拟，常用于虚拟机、VPN 等场景）

---

总线：

- 计算机各部件之间传输数据的公共通道

- 按传输内容分为：数据总线、地址总线、控制总线（常见标准如 PCIe、USB、SATA 等）

---

### 网络通信

从mac地址到ARP表

---

### URL结构

```text
scheme://host:port/path?query#fragment
```

- `scheme`: 协议名

- `host`: 目标主机的域名

- `port`: 端口（每个计算机都会有很多端口用于和外部网络交互）

- `path`: 资源在目标服务器上的路径

- `query`: 查询串（发给服务器的）

- `fragment`: 指向资源内部片段

---

### 工作原理

当输入url，请求会被发给DNS解析服务器

然后DNS解析服务器会根据你输入的域名，查找过后返回对应的IP给浏览器。

浏览器得到IP地址之后，就可以直接访问IP地址所对应的服务器

---

### 终端

打开终端

```bash
#windows

windows + R

输入powershell，然后回车

#macos

command + space

输入terminal.app，然后回车

```

什么是终端

- 物理终端（上古时期）

- 终端模拟器（伪终端）

伪终端分为两端：

- 主端：由终端模拟程序或者远程服务程序控制

- 从端：和与终端交互的程序链接，作为该程序的输入输出

---

在前段时间制作 **Wolf TRX（狼电台）** 时，需要一个 USB-Blaster 编程器给 FPGA 芯片烧录程序，于是在某宝购买了一个。

收到货后，连接电脑可以识别，但始终无法正常使用。多次尝试无果，看起来硬件并没有明显问题，最后只能暂时搁置。

直到最近看到一篇文章，提到可以通过**重新刷写固件**让这类编程器“复活”，于是决定亲自尝试。

---

## 拆机与芯片确认

![某宝购买的编程器拆掉外壳图片](https://img.cattk.com/20241102/AQAD_7sxG4XRAAFXfg.jpg)

> 某宝购买的 USB-Blaster，拆掉外壳后的样子

![正面 - 使用的芯片是 GH552G](https://img.cattk.com/20241102/AQAD_rsxG4XRAAFXfg.jpg)

> 正面，主控芯片为 **GH552G**

![背面](https://img.cattk.com/20241102/AQAD_bsxG4XRAAFXfg.jpg)

> 背面电路布局

---

## 一、下载刷写工具与固件

开始前需要准备刷写工具和固件文件：

- **WCHISPTool（官方刷写工具）**  
  [下载地址](https://www.dropbox.com/scl/fi/174bpr6hi83atrn8znhzi/WCHISPTool_Setup.exe?rlkey=rdyjww4dxrcxmkmlpldggqyfe&dl=0)

- **USB-Blaster 固件（CH552）**  
  [下载地址](https://www.dropbox.com/scl/fi/htm29q7aygb08amn6c5kz/CH552_Blaster_v22.2.27.hex?rlkey=rj66oquduqwv5rr5w5qe68s1s&dl=0)

---

## 二、WCHISPTool 参数设置

安装并打开 **WCHISPTool**，界面如下：

![WCHISPTool 软件界面](https://img.cattk.com/20241102/AQAD_LsxG4XRAAFXfg.jpg)

参数配置步骤：

1. **右侧芯片系列**  
   选择：`E8051 USB 系列 CH54x / CH55x`

2. **左侧芯片型号**  
   - 芯片系列：`CH55x`  
   - 芯片型号：`CH552`

3. **下载文件**  
   选择已下载的 `.hex` 固件文件，并勾选

---

## 三、进入 ISP 下载模式

使用 **镊子或导线** 短接 **D+ 与 3V3 引脚**：

![短接 D+ 和 3V3 引脚](https://img.cattk.com/20241102/AQAD-7sxG4XRAAFXfg.jpg)

操作顺序非常关键：

1. 短接 D+ 与 3V3  
2. 插入 USB 连接电脑  
3. **立即松开短接点**

> ⚠️ 若不及时松开，WCHISPTool 在识别 USB 设备时可能会报错。

---

## 四、刷写并验证固件

当软件成功识别设备后，会显示在 **设备列表** 中：

- 点击 **「下载」** 开始刷写固件
- 刷写完成后，可点击 **「验证」**，确认固件写入正确

整个过程通常只需几秒钟。

---

## 五、刷写完成

刷写完成后，USB-Blaster 即可被系统正常识别，并用于 FPGA 程序烧录。

![刷写完成](https://img.cattk.com/20241102/AQAD-rsxG4XRAAFXfg.jpg)

🎉 **至此，固件重刷完成，设备成功复活。**

---

## 参考与来源

- **参考文章**  
  [ua3reo.ru 原文](https://ua3reo.ru/proshivka-kitajskogo-usb-blaster-na-osnove-ch552g)

- **固件来源**  
  UA3REO（[https://ua3reo.ru](https://ua3reo.ru)）
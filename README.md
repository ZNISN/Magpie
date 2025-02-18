# MAGPIE

Magpie可以将任意窗口放大至全屏，支持多种高级缩放算法，包括Lanczos、[Anime4K](https://github.com/bloc97/Anime4K)、[FSR](https://github.com/GPUOpen-Effects/FidelityFX-FSR)、[FSRCNNX](https://github.com/igv/FSRCNN-TensorFlow)等。

主要用于游戏窗口的放大显示，适用于不支持全屏模式，或者内置的全屏模式会使画面模糊的情况。

使用中遇到问题请提交 issue。

☛ [编译指南](https://github.com/Blinue/Magpie/wiki/编译指南)

☛ [FAQ](https://github.com/Blinue/Magpie/wiki/FAQ)

## 使用方法

![窗口截图](img/窗口截图.png)

要放大的窗口位于前台时，按下热键即可全屏显示该窗口，再次按下热键或者切换前台窗口将退出全屏。

以下为配置说明：

#### 缩放模式

程序预置了多种缩放模式，如果它们不符合你的需求，请[自定义缩放](https://github.com/Blinue/Magpie/wiki/%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BC%A9%E6%94%BE)。

1. Lanczos：常见的传统插值算法，善于保留锐利的边缘。
2. RAVU：见[About RAVU](https://github.com/bjin/mpv-prescalers#about-ravu)。此预置使用zoom变体。
3. FSRCNNX：FSRCNN的变体。在各种场合表现优秀。
4. ACNet：[ACNetGLSL](https://github.com/TianZerL/ACNetGLSL)的移植。适合动画风格的图像和视频放大。
5. Anime4K：开源的高质量的实时动漫缩放/降噪算法。
6. FSR：适用于3D游戏。
7. Integer Scale：将每个像素放大整数倍，可以完整保留原图像的视觉效果。预置了2x和3x两种放大倍率。

#### 抓取模式

指示程序如何抓取源窗口图像

1. WinRT Capture：使用[Screen Capture API](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/screen-capture)抓取窗口，最推荐的方法。此API从Windows 10, v1903开始提供。
2. GDI：使用GDI抓取源窗口，速度稍慢。

#### 注入模式

如果源窗口使用了自定义光标，屏幕上可能出现两个光标。为了解决这个问题，Magpie提供了进程注入的功能：

1. 不使用注入：适用于源窗口没有自定义光标的场合
2. 运行时注入：在执行缩放的同时注入源窗口线程，退出全屏后取消注入
3. 启动时注入：适用于运行时注入不起作用的场合，不能注入正在运行的进程，需要手动选择要启动并注入的程序。

## 使用提示

1. 如果你设置了DPI缩放，而要放大的窗口不支持（表现为画面模糊），请首先进入该程序的兼容性设置，将“高DPI缩放替代”设置为“应用程序”。

   ![高DPI设置](img/高DPI设置.png)

2. 一些游戏支持调整窗口的大小，但只是简单的使用线性缩放，这时请先将其设为原始分辨率。

## 免责声明

因为使用了进程注入技术，本程序有可能被报毒。出于安全考虑，您应该检查源代码并自行编译。开发本程序的初衷不含有任何恶意，但使用它所造成的后果应由您自己承担。

参见[LICENSE](./LICENSE)。
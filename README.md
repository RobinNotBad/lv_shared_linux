## lv_shared_linux

将lvgl编译为 linux 共享库，以减少编译耗时。

已配置了 fbdev 和 evdev，并链接freetype、ffmpeg。

另外，少量修改了 lvgl 源码（比如找不到字符时使用占位符）

## 运行平台
**全志 V833，Tina Linux，musl-libc**

需要注意：lib 文件夹里的 .so 库文件大多由未改动的源码预编译而来，少量是从系统中直接拿取，目标系统为armv7 musleabi hf。

你可以用自己的编译器重新编译这些库，从而适配不同的系统环境。

ffmpeg 需要链接 libz 以实现 png 解码支持。

## 怎么编译源代码
* 建议使用**linux系统**
* 拉取源代码
* 找一个适合设备系统的交叉编译器
> 例如 arm-openwrt-linux-muslgnueabi-gcc
* 将项目文件中 build.sh 中的文件路径改为你的编译器路径
* 运行 ./build.sh 等待编译完成，输出的动态链接库文件在此目录下的 liblvgl.so
* 使用共享库时，用 install/include 目录中的头文件，并链接 liblvgl.so

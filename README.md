# tiny4412
tiny4412开发板学习相关

## 环境搭建
使用QT配置作为基础编译内核
cp tiny4412_core-qt_defconfig .config
make -j4

## 1. LCD相关

### 1.1. 去掉s3c-fb驱动部分
为了更好的理解LCD驱动，首先将内核的LCD驱动去掉。
在drivers/video/Makefile中，注释掉如下部分
```
obj-$(CONFIG_FB_S3C)           += s3c-fb.o
obj-$(CONFIG_FB_S3C2410)       += s3c2410fb.o
```
注意，不要在内核配置中去取消此部分，防止部分头文件以及依赖性函数无法编入内核。

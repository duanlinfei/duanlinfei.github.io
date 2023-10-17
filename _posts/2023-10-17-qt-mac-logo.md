---
layout: post
title: Mac端Qt设置应用图标
categories: [未分类]
---


## 1、下载png格式的图标
这里提供的是[阿里网站的图标库](https://www.iconfont.cn/home/index?spm=a313x.7781069.1998910419.2)

## 2、在某一路径下创建文件夹
这个路径自定，命名为`***.iconset`，后面的**不可省**

如.`logo.iconset`


## 3、将下载的图标.png文件拖进去
记得重新命名。如. logo.png

## 4、打开终端，cd到`***.iconset`
在这里输入指令，制作从16-16到512-512像素的png格式，

记住命名一定要以 `icon_**.png`及`icon_**@2x.png`为模版

否则会出现 fail to generate icns 错误，就是因为这，一度想放弃。

```bash
sips -z 16 16 logo.png --out icon_16.png
sips -z 16 16 logo.png --out icon_16@2x.png

sips -z 32 32 logo.png --out icon_32.png
sips -z 32 32 logo.png --out icon_32@2x.png

sips -z 64 64 logo.png --out icon_64.png
sips -z 64 64 logo.png --out icon_64@2x.png

sips -z 128 128 logo.png --out icon_128.png
sips -z 128 128 logo.png --out icon_128@2x.png

sips -z 256 256 logo.png --out icon_256.png
sips -z 256 256 logo.png --out icon_256@2x.png

sips -z 512 512 logo.png --out icon_512.png
sips -z 512 512 logo.png --out icon_512@2x.png
```

## 5、生成.icns图标
返回上一层目录，执行
```bash
iconutil -c icns logo.iconset 
```

即可在当前路径看见icns格式的文件

## 6、将图片拷贝至工程路径下
xx.pro文件 同级目录

## 7、在.pro文件中最后一行加入语句
`ICON = logo.icns`//自己的图标名

运行即可。

## 8、此时如果仍然没有

那是因为之前运行过一次，生成了文件

内部的Makefile文件并没有改变。

此时只需要将文件夹删除，重新编译即可。

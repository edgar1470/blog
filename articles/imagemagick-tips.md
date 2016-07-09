ImageMagick Tips
<!-- toc -->

### 给图片添加中文字符水印
```bash
  #!/bin/bash
  mogrify -font msyh.ttf -pointsize 64 -fill red -weight bolder -gravity southeast -annotate +20+20 @"t.txt" src.jpg
```
* msyh.ttf 是水印使用的字体,可以指定路径 /font/xx.ttf
* 64 水印字体大小
* t.txt 文件中包含了一行水印描述，字体文件支持的所以编码空间中的字符都可以



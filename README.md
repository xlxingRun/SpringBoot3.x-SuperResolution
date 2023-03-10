# 在线超分辨率网页开发
作者：邢小林 时间：2023-02-27
## 1. 可行性研究
当前存在一些在线超分辨率的网站或工具，主要包括：
- bigjpg - AI人工智能图片无损放大
  - 文件大小 <= 10MB，尺寸<= 3000x3000px
  - 免费版可将图片放大2～4倍，可选不同程度的图片降噪，升级后最大放大16倍。
- 迅捷图片转换器
  - 支持JPG PNG WEBP等图片格式，>32x32px，<1920x1090px
  - 可将图像放大2～4倍。
- waifu2x
  - 文件大小 ≤ 5MB，可降噪图像 ≤ 3000x3000px，可放大图像 ≤ 1500x1500px
  - 可放大1.6倍和2倍
## 2. 需求分析
待补充，可以总结，作为毕业设计的一个部分。
需要包含的功能有
- 支持多种图像格式，包括png、jpg和webp
- 支持规格分辨率，常规值x2 x3 x4，较大分辨率x8，可选x16
- 支持多种超分辨率算法，包括SRCNN RCAN SwinIR等
- 支持批量超分辨率，一批最多支持20张不超过2000x2000分辨率的图片
- 支持访问文件夹和拖拽上传两种方式
- 实时处理时间估计
- 支持在线预览功能
- 支持用户登陆功能
## 3. 设计阶段
### 3.1 整体操作
用户第一次进入页面，可以直接获取服务（使用cookie待考虑）
服务器回传token信息，之后的过程中，所有的操作均需要该token来验证用户身份

1. 用户上传图像给服务器
2. 服务器接收到图像进行解码，超分辨率

开始 -> 上传图像 
  -> 设置参数 -> 开始超分辨率 -> 下载图像
上传图像 -> 上传图像失败，重新上传
    -> 图像尺寸、格式判定，若不符合则上传失败


### 3.1 数据库设计
用户上传图像，图像被存储到特定的文件夹中，然后服务器启动python程序进行超分辨率，完成后返回高分辨率图像。
可以借助云存储，将图像放到具有公网ip的云服务器上，供用户下载。


## 遇到的问题
- @Data注解不起作用，在编译的时候发生错误。
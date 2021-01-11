## 分层和合成机制： 为什么CSS动画比JavaScript高效

## 显示器是怎么显示图像的
- 每秒固定读取60次前缓冲区中的图像，并将读取的图像显示到显示器上
- 显卡的职责是合成新的图像，并将图像保存到后缓冲区中。

## 帧 VS 帧率
- 渲染流水线生成的每一副图片称为一帧
- 把渲染流水线每秒更新了多少帧称为帧率
- 渲染引擎生成某些帧的时间过久，用户就会感受到卡顿
- 解决卡顿，Chrome引入了分层和合成机制。分层和合成机制代表了当今最先进的渲染技术

## 如何生成一帧图像

## 分层和合成
- 将素材分解为多个图层的操作叫做分层，将这些图层合并到一起的操作就称为合成。

## 分块
- 分层从宏观上提升了渲染效率，分块从微观层面上提升了渲染效率
- 合成线程会将每个图层分割为大小固定的图块，然后优先绘制靠近视口的图块，这样就可以大大加速页面的显示速度
- 纹理上传  首次合成图块使用一个低分辨率的图片，当正常比例网页内容绘制完成后，再替换掉当前的显示的低分辨率内容。

## 如何利用分层技术优化代码
- 使用JavaScript对某个元素做几何形状、透明度、缩放等变换操作，绘制效率非常低下。
- 可使用will-change来告诉渲染引擎你会对该元素做一些特效变换
  ```css
  .box { will-change: transform, opacity; }
  ```
- will-change 会提前告诉渲染引擎、让它为该元素准备独立的层。
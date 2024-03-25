用了几个商业的旋转验证码，包括站内其他家开源项目，误差太大，索性自己训练一套，实测某书家旋转验证码预测角度误差基本不超过3度，非常的nice，理论上其他验证码用这个思路也是没有一点问题的，无论双图还是单图旋转。
![image](https://github.com/8yteDance/RotateCaptcha/assets/164896531/9d6e8112-f602-4a08-a0d2-2f8b9cf37990)

大致思路：先标注出尽可能多的图片（label.py）将其旋转到正确角度（0度），然后用图片去重软件去除多余的图片（我懒得自己写，便用了Duplicate Cleaner 5，效果也是非常的棒棒哈），某书大概五六十张原图，将其分别生成旋转成360度的图片，这样就拥有了360个分类，然后对这些数据进行分类训练即可，如果是多图则无需训练背景图，只需要训练中间的图片即可。

代码里已经训练好基于pytorch预测某书的模型，模型很小但是很快很准。

简单做个对比（几十度误差好意思拿出来骗老夫的钱，气得老夫自己训练一个直接开源）：
![image](https://github.com/8yteDance/RotateCaptcha/assets/164896531/4da2c200-3e9d-4e30-b5aa-454ea5b1c980)


最后感谢chat gpt，代码全是chat gpt写的，要抓去抓chat gpt...

test.py是对图像方框中温度进行识别的测试代码，可以针对指定文件夹下的所有带温度的红外图jpg格式文件、bmp位图格式文件分别截取对应位置的温度进行识别，并将文件名和对应温度分行保存为txt文本格式，可见文件result.txt。
按照第一种方案，使用的是PIl库和现有的pyocr工具-tesseract（谷歌开源）。官方的字库识别范围广但精度不够，可使用jTessBoxEditor工具训练num字库来提高针对性。tesseract工具（必须安装，可参考网上教程）及根据图像中温度的数字样式训练好的num字库(num.traineddata)均在当前文件夹中。jTessBoxEditor工具也附带上传,可供使用学习。
测试结果，对于正常图片识别准确率可以达到百分之百，包括带温度的红外图jpg格式文件及bmp位图格式文件。因为在识别前就截取区域进行了灰度化和合适阈值的二值化处理，处理后黑白图片如right.jpg所示，配合num字库完全可以百分百识别。
存在问题：对于直接对设备进行拍摄的jpg图像，识别可能存在误差。原因主要是在识别温度的背景上，可能存在强光束照射，导致预处理后的图像存在大面积噪声，如wrong_1.jpg、wrong_2.jpg所示，很可能误识别为1等数字，导致温度识别的数字位数增加。
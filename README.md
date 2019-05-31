# matplotlib 简介
## matplotlib的pyplot模块简介

   导入： from matplotlib import pyplot
   使用pyplot模块的plot方法进行图表初始化,plot方法接受三个参数:
   
   * x_values:X轴
   * y_values:y轴
   * linewidth:线条宽度

```
pyplot.plot(x_values,y_values,linewidth=5)
pyplot.title('图表标题',fontsize=14) 设置图表标题和字体大小
pyplot.xlable('X轴名'，fontsize=14)
pyplot.ylable('y轴名'，fontsize=14)
pyplot.tick_params(axis='both',lablesize=14) 设置刻度标记大小
pyplot.show() 将图表显示出来
```

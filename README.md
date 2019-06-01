# matplotlib 简介
## matplotlib的pyplot模块简介
### 使用plot()方法画线条
   导入： from matplotlib import pyplot  
   使用pyplot模块的plot方法进行图表初始化,plot()方法接受三个参数:  
   
   * x_values:X轴
   * y_values:y轴
   * linewidth:线条宽度

```python  
pyplot.plot(x_values,y_values,linewidth=5)
pyplot.title('图表标题',fontsize=14) 设置图表标题和字体大小
pyplot.xlable('X轴名'，fontsize=14)
pyplot.ylable('y轴名'，fontsize=14)
pyplot.tick_params(axis='both',lablesize=14) 设置刻度标记大小
pyplot.show() 将图表显示出来
```  
### 使用scatter（）方法画点  
scatter()接受五个参数：  
* X轴坐标  
* Y轴坐标  
* c='red' 设置圆点颜色,可使用RGB模式自定义颜色如：(0,0,0.8)分别用三位0~1之间小数表示红绿蓝，数字越大颜色越浅  
* camp=plot.cm.Blues 设置颜色映射，使颜色进行渐变，渐变依据c参数提供的值，例：c=y表示y轴越大颜色越深
* edgecolor='none' 设置圆点轮廓颜色
* s圆点大小  

```python  
pylot.figure(dpi=128,figsize=(10.6)) 设置屏幕大小，dpi传递分辨率，figsize指出绘图窗口尺寸，单位英寸
pyplot.scatter(x,y,c='red',edgecolor='none',s=200) 其实圆点轮廓颜色默认为None
pyplot.title('图表标题',fontsize=14) 设置图表标题和字体大小
pyplot.xlable('X轴名'，fontsize=14)
pyplot.ylable('y轴名'，fontsize=14)
pyplot.tick_params(axis='both',lablesize=14) 设置刻度标记大小
pyplot.axis([0,1100,0,1100000]) 设置坐标轴的取值范围
pyplot.show() 将图表显示出来  
``` 
> 如果要绘制一系列圆点则只需传入列表参数  

保存图表  
`pyplot.savefig('file.png',bbox_inches='tight')`  
> 第一个参数表示图片名，第二参数设置是否要边框  

隐藏坐标轴  
```
pyplot.axes().get_xaxis().get_visible(False)  
pyplot.axes().get_xaxis().get_visible(False)  
```
> 通过将每条坐标轴的可见性设置为False来隐藏坐标轴  

# 使用Pygal工具创建图表 详情访问http://www.pygal.org/  


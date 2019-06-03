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
`pylot.fill_between(dates,highs,lows,facecolor='blue',alpha=0.1)`  
> 方法fill_between()接受一个X轴系列和两个Y轴系列，并填充两个Y轴系列之间的空间，
> alpha值设置颜色透明度，0表示完全透明  

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
## 绘制直方图  
```Python  
import pygal  
hist = pygal.Bar() 进行Pygal实例化,实例化为直方图  
hist.title = "Result of rolling one D6 1000 times" 设置直方图标题  
hist.x_lables = ['1','2','3','4','5','6'] 设置X轴刻度  
hist.x_title = "Result" X轴名  
hist.y_title "Frequency of result" Y轴名  

hist.add('D6',frequencies) 添加直方图名‘D6’，以及传入参数列表frequencies  
hist.render_to_file('die_visual.svg') 将最后图像保存为svg文件  
```  
> svg文件可以使用浏览器打开，并具有一定互动性。Y轴刻度会根据数据自动设置  
```  
import pygal  
line_chart = pygal.Line(x_lable_rotation=20,show_minor_x_labels=False)  实例化折线图
line_chart.title = '收盘价'  折线图标题
line_chart.x_labels = dates  设置折线图X轴刻度
N = 20  X轴每隔20天显示一次
line_chart.x_labels_major = dates[::N]  配置X轴major属性，每隔20天显示一次，这样X轴不会过于拥挤
line_chart.add('收盘价'，close)  
line_chart.render_to_file('收盘价折线图.svg')  
```  
## pygal 样式  
从pygal.style模块中能导入各种样式例如：  
LightColorizedStyle , LightenStyle  
```  
my_style = LightenStyle('#333366',base_style=LightColorizedStyle)  
```  
> 将my_style传入pygal.Bar()中的style参数，设置基色为深蓝  
```  
my_config = pygal.Config()  设置config实例，定制图表外观  
my_config.x_label_rotation = 45  X轴字体旋转角度
my_config.show_legend = False  
my_config.title_font_size = 24  设置标题字体大小
my_config.label_font_size = 14  副标签
my_config.major_label_font_size = 18  主标签
my_config.truncate_label = 15  将较长项目缩短为15个字符，将鼠标放上去则会全部显示  
my_config.show_y_guides = False  隐藏图表水平线
my_config.width = 1000  自定义宽度，以充分利用浏览器空间

chart = pygal.Bar(my_config,style=my_style)  
...
```  


# 获取数据  
## CSV文件  
> CSV 文件是一系列以逗号分隔的值组成的数据，要操作CSV文件可以导入CSV模块  
```Python  
import CSV  
filename = '文件名.csv'  
with open(filename) as f:
   reader = csv.reader(f) 调用reader（）方法读取csv文件  
   header_row = next(reader) 再调用next（）读取一行文件，可加入for循环进行逐行读取  
   print(header_row)  
   ```  
   > 读取数据后将数据加入列表，并将此列表传入制图工具，工具将以此文件进行绘图  
   
## JSON格式文件  
```Python  
import json 

filename = 文件.json  
with open(filename) as f:
   data = json,load(f)  
for d in data:  
   a = d['']  
   ...  
   ```  
> json.load() 方法将json文件读取为字典类型文件，后面则以操作字典的方法获取文件信息

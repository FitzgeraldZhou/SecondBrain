#matplotlib #matplotlib/pyplot 
常用的绘图模块，提供和MATLAB类似的2D绘图API
```python
import matplotlib.pyplot as plt
```

## pyplot.plot()
#matplotlib/pyplot/plot
用于绘制散点图和线图
```python
pyplot.plot(x, y, [fmt], *, data=None, **kwargs)
pyplot.plot(x, y, [fmt], x2, y2, [fmt2], ..., **kwargs)
```
- x, y：两坐标轴数据，列表或数组
> 当只指定y轴上的点时，x会自动设置为**0, 1, 2, ..., N - 1**，其中N为y数组/列表中元素的个数
- \[fmt\]：可选，定义基本格式（线条样式、颜色、标记等）
- \*\*kwargs：可选，用于在二维平面图上，设置指定属性（标签、线的宽度等）

#### fmt
#matplotlib/pyplot/plot/fmt

```python
fmt = '[marker][line][color]'
```
##### 颜色参数
#matplotlib/pyplot/plot/fmt/color
- 'b'：蓝色
- 'g'：绿色
- 'r'：红色
- 'y'：黄色
- 'k'：黑色
- 'w'：白色
- 'm'：洋红色
- 'c'：青绿色
- 'SeaGreen'：深绿色
- '#0x008000'：RGB颜色字符串

>多条曲线不选色颜色时，默认会自动选择不同的颜色用来区分

##### 线型参数
#matplotlib/pyplot/plot/fmt/line
- '-'：实线
- '--'：破折线
- ':'：虚线
- '-.'：点划线

##### 标记字符
#matplotlib/pyplot/plot/fmt/marker
定义标记形状
- 'o'：实心圆标记，大
- '.'：点标记，中
- ','：像素点标记，小
- 'v'：倒三角标记
- '^'：上三角标记
- '>'：右三角标记
- '<'：左三角标记
- '\$f\$'：渲染指定字符，例如用字母f为标记
###### markersize
#matplotlib/pyplot/plot/fmt/marker/markersize 
简写为**ms**，定义标记大小

###### markerfacecolor
#matplotlib/pyplot/plot/fmt/marker/markerfacecolor
简写为mfc，定义标记内部颜色
> 同fmt中的color -> [[Pyplot#fmt#颜色参数]]

###### markeredgecolor
#matplotlib/pyplot/plot/fmt/marker/markeredgecolor
简写为mec，定义标记边框颜色
> 同fmt中的color -> [[Pyplot#fmt#颜色参数]]

#### \*\*kwargs
#matplotlib/pyplot/plot/kwargs
绘图过程中自定义线的样式（类型、颜色、大小等）

##### 线的类型
#matplotlib/pyplot/plot/kwargs/linestyle
线的类型用linestyle来定义，简写为**ls**

|  类型  |  简写  |  描述  |
|-------|-------|-------|
|'solid' (默认)|'-'|实线|
|'dotted'|':'|点虚线|
|'dashed'|'--'|破折线|
|'dashdot'|'-.'|点划线|
|'None'|'' 或 ' '|不画线|
##### 线的颜色
#matplotlib/pyplot/plot/kwargs/color
线的颜色用color来定义，简写为**c**
> 同fmt中的color -> [[Pyplot#fmt#颜色参数]]


##### 线的宽度
#matplotlib/pyplot/plot/kwargs/linewidth 
线的宽度可以使用linewidth来定义，简写为**lw**

### 轴标签和标题
#### xlabel() & ylabel()
#matplotlib/pyplot/plot/label 
使用xlabel()方法和ylabel()方法来定义轴标签
```python
plt.xlabel('xxx')
```

##### fontproperties
#matplotlib/pyplot/plot/label/fontproperties 
设置标签的字体（一般是下载的系统内未内置的字体，提供其系统路径）
```python
font1 = matplotlib.font_manager.FontProperties(fname="xxx.otf")
plt.xlabel('xxx', fontproperties=font1)
```
###### fname
#matplotlib/pyplot/plot/label/fontproperties/fname
下载的字体库的系统路径

- 使用系统字体
1. 先查看系统中所有字体的名字
```python
from matplotlib import pyplot as plt
import matplotlib as mlb
a = sorted([f.name for f in matplotlib.font_manager.fontManager.ttflist])

for i in a:
	print(i)
```
2. 设置字体
```python
plt.rcParams['font.family'] = ['FangSong']
```

##### loc
#matplotlib/pyplot/plot/label/loc
设置坐标轴标签显示的位置
- xlabel()：**'left', 'right', 'center'**,默认为'center'
- ylabel()：**'top', 'bottom', 'center'**,默认为'center'
#### title()
#matplotlib/pyplot/plot/title
##### fontproperties
#matplotlib/pyplot/plot/title/fontproperties
> 同[[Pyplot#xlabel() & ylabel()#fontproperties]]

##### loc
#matplotlib/pyplot/plot/title/loc
设置标题显示的位置
- 'left', 'right', 'center'，默认为'center'

### 网格线
#matplotlib/pyplot/plot/grid
使用grid()方法设置图表中的网格线
```python
plt.grid(b=None, which='major', axis='both', **kwargs)
```
- b：可选，默认为 None，可设置布尔值，**true为显示网格线，false为不显示网格线**，==如果设置\*\*kwargs参数，则值为true==
- which：可选，可选值为'major', 'minor', 'both'，默认为'major'，表示**应用更改的网格线**
- axis：可选，可选值为'x', 'y', 'both'，表示**网格线的方向**
- \*\*kwargs：可选，设置网格格式，同[[Pyplot#* *kwargs]]

### 绘制多个子图

#### suptitle()
#matplotlib/pyplot/suptitle
为整个绘图区域标题
```python
plt.suptitle('xxx')
```

#### subplot()
#matplotlib/pyplot/subplot
```python
plt.subplot(nrows, ncols, index, **kwargs)
```
- nrows：将绘图区域划分为nrows行
- ncols：将绘图区域划分为ncols列
- index：按照从左到右、从上到下的顺序对每个子区域进行编号
	> 例如 
	> 	index = 1：子图坐标为(1, 1)
	>     index = 2：子图坐标为(1, 2)
	>     ...
- \*\*kwargs：同[[Pyplot#* *kwargs]]

##### 实例
```python
import matplotlib.pyplot as plt
import numpy as np
%matplotlib inline

# plot 1
x = np.array([1, 7])
y = np.array([43, 25])
plt.subplot(2, 2, 1)
plt.plot(x, y)
plt.title('plot 1')

# plot 2
x = np.arange(0, 20)
y = x ** 2 / 2
plt.subplot(2, 2, 2)
plt.plot(x, y)
plt.title('plot 2')

# plot 3
x = np.arange(0, 4 * np.pi, 0.1)
y = np.sin(x)
plt.subplot(2, 2, 3)
plt.plot(x, y)

# plot 4
x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])
plt.subplot(2, 2, 4)
plt.plot(x,y)

plt.suptitle("Test")
```
![[image-20230918190926568.png]]


#### subplots()
#matplotlib/pyplot/subplots
```python
plt.subplots(nrows=1, ncols=1, *, sharex=False, sharey=False, squeeze=True, subplot_kw, gridspec_kw, **fig_kw)
```
- nrows：默认为1，设置图表行数
- ncols：默认为1，设置图表列数
- sharex、sharey：设置子图x/y轴是否共享属性，默认为False。可设置的字段有：
	- False或'none'：子图互相独立，不共享任何属性
	- True或'all'：所有子图共享x/y轴
	- 'col'：每个**子图列**共享x/y轴
	- 'row'：每个**子图行**共享x/y轴
- [ ] squeeze：布尔值，默认为True，表示额外的维度从**返回的Axes轴对象中挤出**：
	- 对于N\*1或1\*N个子图，-> 返回一个一维数组
	- 对于N\*M(N>1, M>1)个子图 -> 返回一个二维数组
	- 如果设置为False：不进行挤压操作，返回一个元素为Axes实例的二维数组，即使最终是1\*1  
- subplot_kw：字典类型，将字典关键字传递给add_subplot()函数来创建每个子图
- gridspec_kw：字典类型，将字典关键字传递给GridSpec构造函数创建子图在网格(grid)中
- \*\*fig_kw：将详细的关键字传递给figure()函数

##### 实例
```python
import matplotlib.pyplot as plt
import numpy as np

# 创建一些测试数据 
x = np.linspace(0, 2*np.pi, 400)
y = np.sin(x**2)


# 创建四个子图
fig, axs = plt.subplots(2, 2, subplot_kw=dict(projection="polar"))
axs[0, 0].plot(x, y)
axs[1, 1].scatter(x, y)
```
![[image-20230918192710364.png]]

### 散点图
#### scatter()
#matplotlib/pyplot/scatter
```python
pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None, plotnonfinite=False, data=None, **kwargs)
```
- x、y：维数相同(长度相同)的数组，作为输入数据
- s：点的大小，默认为20，与[[Pyplot#fmt#markersize]]类似
- c：点的颜色，默认为'b'，与[[Pyplot#颜色参数]]类似
- marker：点的样式，默认为'o'，与[[Pyplot#标记字符]]类似
- 
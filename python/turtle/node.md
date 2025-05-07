>最近心血来潮，想学`python`。况且新博客需要大量插入图片，于是敲代码数十小时，遂得此篇。
---
## 代码如下：
```py
import turtle

def box(t,x,y,a,b,r):
    t.up()
    t.goto(x-a/2,y-b/2-r)
    t.down()

    for i in range(2):
        t.forward(a)
        t.circle(r,90)
        t.forward(b)
        t.circle(r,90)

def node(t,x,y,a,b,r):
    box(t,x,y+b/2+r,a,b,r)
    box(t,x,y-b/2-r,a,b,r)

if __name__ == "__main__":
    t=turtle.Turtle()

    node(t,0,0,100,50,15)

    turtle.done()
```
---
## 实现效果
![一个似像不像的节点](https://i-blog.csdnimg.cn/direct/34e6a85cd06d4feba41dc7ab2f3e551d.png#pic_center)

---
# 具体思路

画**节点**，需要两个盒子；画**盒子**，可以画矩形，三角形，正方形等等，这里拿**圆角矩形**来作示范。
要画圆角矩形，我们需要有五个参数，即**长**$a$，**宽**$b$，**半径**$r$，**横坐标**$x$，**纵坐标**$y$。
但是有**两个细节问题**：
$1.$ **长是外接矩形的长吗？**
$2.$ **横纵坐标是这个盒子的中心吗？**
这篇博客中，我们是**这么**处理的：
$1.$ **长不是外接矩形的长。**
$2.$ **横纵坐标是这个盒子的中心。**
所以下面的步骤就很好想了，请见下文。

---
# 逐行代码解析
##### 一、库的调用
>首先要感谢$python$自带的组件里面就有`turtle`库，再也不需要~~万恶的~~$pip$ $install$了，所以我们可以用下面的代码**直接调用**`turtle`库：
```py
import turtle
```
一般地，调用库的方式为```import <name>```
##### 二、box函数
>这个函数是画**盒子**用的。
```py
def box(t,x,y,a,b,r):
    t.up()
    t.goto(x-a/2,y-b/2-r)
    t.down()

    for i in range(2):
        t.forward(a)
        t.circle(r,90)
        t.forward(b)
        t.circle(r,90)
```
>$python$语法： 
>$1.$ `def 函数名name (参数列表list):`，自定义函数。
>我需要调用**五个图形参数**外加**一个画笔参数**
>所以下面的**函数**是这么写的：
```py
def box(t,x,y,a,b,r):
# t->画笔; x->横坐标; y->纵坐标; a->长; b->宽; r->半径
```
>$turtle$接口调用（**这里是平移画笔至想要的位置**）：
>$1.$ `up()`，抬起画笔，此时画笔不会写下东西。
>$2.$ `goto(x,y)`，将画笔沿直线平移到`(x,y)`。
>$3.$ `down()`，落下画笔，此时画笔可以开始写东西。
```py
    t.up()
    t.goto(x-a/2,y-b/2-r)
    t.down()
```
>$python$语法：
>$1.$ `for i in range(2):`，一种循环语句，将$i$从$0$执行到$1$。
>$turtle$接口调用（**这里是画圆角矩形**）：
>$1.$ `forward(d)`，画笔向当前方向走$d$步。
>$2.$ `circle(r,rad)`，画笔向当前方向，以$r$为半径，向左画一个角度为$rad$的圆弧。
```py
    for i in range(2):
        t.forward(a)
        t.circle(r,90)
        t.forward(b)
        t.circle(r,90)
```
##### 三、node函数
>定义了一个$node$函数，这个函数是画**节点**用的。
>函数列表传输了**六个变量**：
>`t->画笔;x->横坐标;y->纵坐标;a->长;b->宽;r->半径`
>再调用$box$函数画两个盒子（~~我真是个天才~~ ）
>**具体代码如下**：
```py
def node(t,x,y,a,b,r):
    box(t,x,y+b/2+r,a,b,r)
    box(t,x,y-b/2-r,a,b,r)
```
##### 四、main函数
>主函数，**无需多言**。
>$1.$ 调用`turtle.Turtle()`获得**画笔**。
>$2.$ 调用`node()`，在合适的位置画出**节点**。
>$3.$ `turtle.done()`，是$turtle$图形库的一个方法，用于标志绘图任务的结束，并保持绘图窗口开启，直到用户主动关闭。
```py
if __name__ == "__main__":
    t=turtle.Turtle()
    
    node(t,0,0,100,50,15)

    turtle.done()
```
---
# 后记
懒得写后记 $AwA$ 。

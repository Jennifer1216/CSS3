# CSS3
#### css3绘制特三角形
原理：将宽度、高度设为0，将一边颜色显示出来，其它边颜色设为透明
```css
/*纯css绘制向上三角形*/
#triangle-up { 
  width: 0; 
  height: 0; 
  border-left: 50px solid transparent; 
  border-right: 50px solid transparent; 
  border-bottom: 100px solid red;
}
```
```css
/*纯css绘制向右三角形*/
#triangle-left { 
  width: 0; height: 0; 
  border-top: 50px solid transparent; 
  border-right: 100px solid red; 
  border-bottom: 50px solid transparent;
}
```
需要什么方向的三角形，就将其方向设为可见，其它设为transparent，大家可以去试试
#### 五角星
- 三个同样三角形拼接而成，利用css3属性的transform旋转,接下来，咱来绘制第一个三角形
```css
#star {
  margin: 50px auto 0;
  position: relative;
  display: block;
  width: 0;
  height: 0;
  border-right: 70px solid transparent;
  border-left: 70px solid transparent;
  border-bottom: 40px solid #c889ff;
}
```
![pict](http://p3.pstatp.com/large/46fd00035a34993483c0)
- 利用伪类，在之前绘制第二个三角形，根据第一个进行旋转，我用笔算了一下，旋转72deg,可达到效果
```css
#star:before {
  position: absolute; 
  top:0; 
  left:-74px; 
  content: ''; 
  display: block; 
  width: 0; 
  height: 0; 
  border-right: 70px solid transparent; 
  border-left: 70px solid transparent;
  border-bottom: 40px solid #c889ff; 
  -webkit-transform: rotate(72deg); 
  -moz-transform: rotate(72deg); 
  -ms-transform: rotate(72deg); 
  -o-transform: rotate(72deg); 
  transform: rotate(72deg);
}
```
![pic](http://p3.pstatp.com/large/46ff00013aaa49c2e169)
- 第二个三角形绘制出来 ，第三个就迎刃而解了，只需在第二个三角形的基础上，将其反转（旋转-72deg）
```css
#star:after { 
  position: absolute; 
  top:0; 
  left:-70px; 
  content: ''; 
  display: block; 
  width: 0; 
  height: 0; 
  border-right: 70px solid transparent; 
  border-left: 70px solid transparent; 
  border-bottom: 40px solid #ffb065; 
  -webkit-transform: rotate(-72deg); 
  -moz-transform: rotate(-72deg); 
  -ms-transform: rotate(-72deg); 
  -o-transform: rotate(-72deg); 
  transform: rotate(-72deg);
}
```
![pict](http://p1.pstatp.com/large/46fb0003b0434af6b8ad)
- 此时，将颜色设置为一样，视觉效果就截然不同了
![pict](http://p3.pstatp.com/large/46fe0001e3c658284651)
#### 吃豆豆
- 原理：利用border-radius和三角形原理，绘制上，下，左，右四个三角形，将右边的颜色设为透明
```css
.eat-man {
  width: 0px;
  height: 0px;
  border:60px solid #e8ff84;
  border-right-color:transparent;
  -webkit-border-radius: 60px;
  -moz-border-radius: 60px;
  border-radius: 60px;
}
```
![pict](http://p3.pstatp.com/large/46f90003ec8d66b77e36)
- 接下来绘制眼睛和豆豆，这就很简单了，眼睛可以利用定位，豆豆我们为其使结构更简单，可以利用伪类
```css
.eat-man {
position: relative;
margin:50px auto 0;
width: 0px;
height: 0px;
border:60px solid #e8ff84;
border-right-color:transparent;
-webkit-border-radius: 60px;
-moz-border-radius: 60px;
border-radius: 60px;} 
/*eye*/
.eat-man .eye {
position: absolute;
top:-50px;
left:0px;
width: 15px;
height: 15px;
background: #fff;
border-radius: 50%;
} 
/*豆豆*/
.eat-man .food:before {
position: absolute;
top:-5px;
left:50px;
content: '';
display: block;
width: 15px;
height: 15px;
background: #fff670;
border-radius: 50%;
}
.eat-man .food:after {
position: absolute;
top:-5px;
left:80px;
content: '';
display: block;
width: 15px;
height: 15px;
background: #fff670;
border-radius: 50%;
}
<div class="eat-man"> <p class="eye"></p> <p class="food"></p> </div>
```
![pict](http://p3.pstatp.com/large/46fd000395a2b66063a4)

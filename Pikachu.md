教你画皮卡丘，首先需要用CSS画出皮卡丘，然后调用函数一步一步执行语句，最后呈现连续效果。
下面是皮卡丘的HTML和CSS样式

- HTML
```
  <div class="preview-wrapper">
    <div class="preview">
      <div class="wraper">
		  <div class="lower_lip_wraper">
			<div class="lower_lip"></div>
		  </div>
		  <div class="nose"></div>
		  <div class="eye left"></div>
		  <div class="eye right"></div>
		  <div class="face left"></div>
		  <div class="face right"></div>
		  <div class="upper_lip left"></div>
		  <div class="upper_lip right"></div>
	  </div>
    </div>
  </div>
```
- 设置盒模型
```
*{
margin:0;
padding:0;
box-sizing:border-box;
}
*::after,*::before{
  box-sizing:border-box;
}
```
- 通过flex布局形成绝对居中的效果：
```
body{
  height:100vh;
  border:1px solid green;
  display:flex;
  justify-content:center;
  align-items:center;
}
```
- 通过相对定位和绝对定位，形成水平居中；
```
.wrapper{
  width:100%;
  height:165pxx;
  border:1px solid red;
  position:relative;
}
.nose{
  width:22px;
  height:22px;
  position: absolute;
  left: 50%;
  top: 28px; 
  border:1px solid black;
}
```
- 画鼻子
```
.nose{
  width:0px;
  height:0px;
  border:12px solid;
  border-color: black transparent transparent; 
  border-radius: 11px;
  margin-left:-11px;
}
```
- 画眼睛
```
画外圆
.eys{
   width:49px;
   height:49px;
   background-color: #2e2e2e;
   position: absolute;
   border-radius:50%;
   border:2px solid #000;
}
画内圆，眼珠
 .eye::before{
   content:'';
   display:block;
   width:24px;
   height:24px;
   background: #fff;
   position: absolute;
   border-radius:50%;
   left:6px;
   top:-1px;
   border: 2px solid #000;
 }
```
- 左右眼睛分开
```
 左眼
 .eye.left{
   right:50%;
   margin-right:90px;
 }
 右眼
 .eye.right{
   left:50%;
   margin-left:90px;
 }
```
- 画脸蛋
```
 .face {
   width:68px;
   height:68px;
   background-color: #fc0d1c;
   position: absolute;
   border-radius:50%;
   border:2px solid black;
   top:85px;
 }
- 左边红晕
 .face.left{
   right:50%;
   margin-right:116px;
 }
- 右边红晕
 .face.right{
   left:50%;
   margin-left:116px;
 }
```

- 画嘴唇
```
先画一个框
 .upper_lip{
   position: absolute;
   height:25px;
   width:65px;
   border:2px solid black;
   border-top:none;
   top:46px;
  background-color: #fee433;/*设置和背景一样的颜色*/
 }
设置弧度和旋转
- 左弧度
 .upper_lip.left{
   border-right:none;
   border-bottom-left-radius:40px 25px;
   transform:rotate(-20deg);
   right:50%;
 }
- 右弧度
 .upper_lip.right{
   border-left:none;
   border-bottom-right-radius:40px 25px;
   transform:rotate(20deg);
   left:50%; 
 }
```
- 画嘴巴
```
先画嘴巴
.lower_lip{
   width:300px;
   height:3500px;
   background-color: #990513;
   border:2px solid black;
   border-radius:200px/2000px;
   position: absolute;
   bottom:0;
   overflow: hidden;
 }
画框限制嘴巴大小
 .lower_lip_wraper{
   position: absolute;
   left:50%;
   margin-left:-150px;
   bottom:0;
   height:110px;
   width:300px;
   overflow: hidden;
 }
```
- 画舌头
```
 .lower_lip::after{
   content:"";
   position: absolute;
   bottom:-20px;
   width:100px;
   height:100px;
   background-color: #FC4A62;
   left:50%;
   margin-left:-50px;
   border-radius:50px;
 }
```



---
title: 进击的前端开发（HTML5 动画介绍）
date: 2019-04-01 13:28:39
tags: 
- HTML
- JavaScript
categories: 
- 前端
---
## HTML5 动画介绍

#### 1.前言
在 Web 开发中，经常需要实现各种动画效果，例如：移动、变形、透明度变化等，今天我们主要来讨论各种移动的实现。
在html5中常用的实现动画的方式主要有：Canvas，SVG Animation和CSS Transform,今天我们主要介绍的是Canvas

### Canvas
#### 2.Canvas简介
canvas是html5提供的一个新的功能！至于作用，就是一个画布。然后画笔就是javascript。canvas的用途非常的广，特别是html5游戏以及数据可视化这两个方面，可以不用太厉害，但是必须要会基础的用法。但是以后对canvas的需求，肯定会越来越大。所以canvas很值得学习，而且学好canvas,就是很好的一个加分项。不过,‘<'canvas'>'元素本身并没有绘制能力（它仅仅是图形的容器),必须使用脚本来完成实际的绘图任务。getContext() 方法可返回一个对象，该对象提供了用于在画布上绘图的方法和属性。


#### 3.常用函数

##### 3.1基础函数
context.moveTo(x,y)
把画笔移动到x,y坐标，建立新的子路径。

context.lineTo(x,y)
建立上一个点到x,y坐标的直线，如果没有上一个点，则等同moveTo(x,y)，把（x,y）添加到子路径中。

context.stroke() 
描绘子路径.

beginPath()
清空子路径，一般用于开始路径的创建。在几次循环地创建路径的过程中，每次开始创建时都要调用beginPath函数。

closePath()
如果当前子路径是打开的，就关闭它。否则把子路径中的最后一个点和路径中的第一个点连接起来，形成闭合回路。

##### 3.2绘制图像
context.drawImage(image,x,y)
把image图像绘制到画布上x,y坐标位置。

context.drawImage(image,x,y,w,h)
把image图像绘制到画布上x,y坐标位置，图像的宽度是w,高度是h。

context.drawImage(image,sx,sy,sw,sh,dx,dy,dw,dh)
截取image图像以sx,sy为左上角坐标，宽度为sw,高度为sh的一块矩形区域绘制到画布上以dx,dy坐标位置，图像宽度是dw,高度是dh。

##### 3.3艺术文字
context.fillText(text,x,y,[maxWidth])
在canvas上填充文字，text表示需要绘制的文字，x,y分别表示绘制在canvas上的横，纵坐标，最后一个参数可选，表示显示文字的最大宽度，防止文字显示溢出。

context.strokeText(text,x,y,[maxWidth])
在canvas上描边文字，参数的意义同fillText


#### 4.Canvas的简单应用
利用canvas绘画出如图所以的环形html5时钟，
![avatar](../html/48B21005-4DCF-4452-B74E-06A5D971918D.png)

主要函数：context.arc(x,y,r,sAngle,eAngle,counterclockwise);
![avatar](../html/56F4CD73-005D-4DAA-95A5-DABE4DE3026D.png)

主要代码如下：

		function degToRad(degree){
			var factor = Math.PI/180;
			return degree*factor;
		}
		function renderTime(){
			var now = new Date();
			var today = now.toDateString();
			var time = now.toLocaleTimeString();
			var hrs = now.getHours();
			var min = now.getMinutes();
			var sec = now.getSeconds();
			var mil = now.getMilliseconds();
			var smoothsec = sec+(mil/1000);
      		var smoothmin = min+(smoothsec/60);

			//Background
			gradient = ctx.createRadialGradient(250, 250, 5, 250, 250, 300);
			gradient.addColorStop(0, "#03303a");
			gradient.addColorStop(1, "black");
			ctx.fillStyle = gradient;
			//ctx.fillStyle = 'rgba(00 ,00 , 00, 1)';
			ctx.fillRect(0, 0, 500, 500);
			//Hours
			ctx.beginPath();
			ctx.arc(250,250,200, degToRad(270), degToRad((hrs*30)-90));
			ctx.stroke();
			//Minutes
			ctx.beginPath();
			ctx.arc(250,250,170, degToRad(270), degToRad((smoothmin*6)-90));
			ctx.stroke();
			//Seconds
			ctx.beginPath();
			ctx.arc(250,250,140, degToRad(270), degToRad((smoothsec*6)-90));
			ctx.stroke();
			//Date
			ctx.font = "25px Helvetica";
			ctx.fillStyle = 'rgba(00, 255, 255, 1)'
			ctx.fillText(today, 175, 250);
			//Time
			ctx.font = "25px Helvetica Bold";
			ctx.fillStyle = 'rgba(00, 255, 255, 1)';
			ctx.fillText(time+":"+mil, 175, 280);
		}
		
		
#### 5.canvas动画实例
利用HTML5 Canvas技术实现的万花筒动画特效，动画开始时，逐渐生成一些随机颜色的矩形方块，然后就不停的旋转，就像万花筒一样，矩形方块越来越小。
如图：
![avatar](../html/ac3c8e80-d9c1-4dcc-9c55-ad373b06d5fb.png)

主要代码：

	window.onload=function(){
			var canvas = document.getElementById("canvas");
			var context = canvas.getContext("2d");
			var rects= [];
			context.translate(200,200);
			setInterval(function(){
				context.clearRect(-200,-200,400,500);
				for(var i=0;i<rects.length;i++){
					context.save();
					//	旋转当前绘图
					context.rotate(rects[i].angle * Math.PI / 180);
					//	缩放当前绘图
					context.scale(rects[i].scale,rects[i].scale);
					context.beginPath();
					context.fillStyle=rects[i].color;
					context.rect(rects[i].len,rects[i].len,50,50);
					context.fill();
					//	返回之前保存过的路径状态和属性
					context.restore();
				}
			},60);
			setInterval(function(){
				rects.push(createRect());
			},1000);
			setInterval(function(){
				for ( var i = 0; i < rects.length; i++) {
					rects[i].len = rects[i].len -0.2;
					if(rects[i].len <= 0){
						rects.splice(i,1);
						continue;
					}
					rects[i].scale = rects[i].scale - 0.002;
					if(rects[i].scale <= 0.2){
						rects[i].scale = 0.2;
					}
					rects[i].angle = rects[i].angle+2;
					if(rects[i].angle >=360){
						rects[i].angle =0;
					}
					
				}
			},60);
		};

	function createRect(){
		var rect = {
				len:150,
				scale:1,
				angle:0,
				color:"rgb("+getRandom()+","+getRandom()+","+getRandom()+")"
		};
		return rect;
	}
	function getRandom(){
		return Math.floor(Math.random()*255);
	}

>setTimeout() 实现的动画和 requestAnimationFrame() 实现的动画的区别


#### 6. THREE.JS 和Canvas
##### 6.1 three.js是做什么的
webGL基于光栅化的2D API，封装成了我们人类能看懂的 3D API。

1.辅助我们导出了模型数据；

2.自动生成了各种矩阵；

3.生成了顶点着色器；

4.辅助我们生成材质，配置灯光；

5.根据我们设置的材质生成了片元着色器。

>开源地址：https://github.com/mrdoob/three.js

##### 6.2 three.js三大组件
###### 渲染器（Renderer）
渲染器将和Canvas元素进行绑定

    var renderer = new THREE.WebGLRenderer({
    	canvas: document.getElementById(‘mainCanvas’)
    });
如果想要Three.js生成Canvas元素，在HTML中就不需要定义canvas，在js中可以这样写：

    var renderer = new THREE.WebGLRenderer();
    renderer.setSize(400,300);
    document.getElementsByTagName(‘body’[0].appendChild(renderer.domElement);
    renderer.setClearColor(0x000000);
    
###### 场景（Scene）
　在Three.js中添加的物体都是添加到场景中的。在程序最开始的时候进行实例化，然后将物体添加到场景中即可。

    var scene = new THREE.Scene();
###### 照相机（Camera）
webGL和Three.js使用的坐标系是右手坐标系：
![avatar](../html/899901-20160725133656700-2000808953.png)
相机分正投影相机和透视投影相机。这里先定义一直透视投影的照相机

    var camera = new THREE.PerspectiveCamera(45,4/3,1,1000);
    //四个参数分别对应：视角、近处的裁面的距离、远处的裁面的距离、实际窗口的纵横比（后面会详细讨论）
    camera.position.set(0,0,5);//设置相机位置
    scene.add(camera);//添加到场景中
###### 渲染
在定义了场景中的物体，设置好的照相机之后，渲染器就知道如何渲染出二维的结果了。调用渲染器的渲染函数，就能使其渲染一次了

    renderer.render(scene, camera);
    
    
##### 6.3 three.js案例

    <!DOCTYPE html>

    <html>

    <head>

    <meta charset="UTF-8">

    <title>3.js测试一</title>

    </head>

    <body onload="init()">

    <canvas id="mainCanvas" width="400px" height="300px" ></canvas>

    <script type="text/javascript" src="js/three.min.js"></script><!--路径改成你的-->

        <script type="text/javascript">

            function init() {

                // renderer 渲染器

                var renderer = new THREE.WebGLRenderer({

                    canvas: document.getElementById('mainCanvas')　　//绑定canvas

                });

                renderer.setClearColor(0x000000); // black 

                

                // scene 场景

                var scene = new THREE.Scene();　　//实例化场景

                

                // camera 照相机

                var camera = new THREE.PerspectiveCamera(45, 4 / 3, 1, 1000);　　//透视投影相机参数设置

                camera.position.set(0, 0, 5);　　//相机位置设置

                scene.add(camera);　　//添加到场景

                

                // a cube in the scene 创建的物体

                var cube = new THREE.Mesh(new THREE.CubeGeometry(1, 2, 3),　　//创建网格，参数一：几何体（立方体）

                        new THREE.MeshBasicMaterial({　　//参数二：材质（网格基础材质）

                            color: 0xff0000　　//设置颜色

                        })

                );

                scene.add(cube);　　//添加到场景

 

                // render 渲染

                renderer.render(scene, camera);

            }

        </script>

    </body>

    </html>
    
>three.js初始化方法为init()














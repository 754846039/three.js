# Face3对象定义Geometry的三角形面

## Face3构建三角形
```javascript
var geometry = new THREE.Geometry(); //声明一个几何体对象Geometry
// 两个三角形6个顶点，两个重合
var p1 = new THREE.Vector3(0, 0, 0); //顶点1坐标
var p2 = new THREE.Vector3(0, 100, 0); //顶点2坐标
var p3 = new THREE.Vector3(50, 0, 0); //顶点3坐标
var p4 = new THREE.Vector3(0, 0, 100); //顶点4坐标
//顶点坐标添加到geometry对象
geometry.vertices.push(p1, p2, p3,p4);

// Face3构造函数创建一个三角面
var face1 = new THREE.Face3(0, 1, 2);//顶点索引值

```
## 三角形法线设置
#### 1.定义三角形三个顶点的法线方向数据来表示三角形面法线方向
```javascript
//三角面每个顶点的法向量
var n1 = new THREE.Vector3(0, 0, -1); //三角面Face1顶点1的法向量
var n2 = new THREE.Vector3(0, 0, -1); //三角面2Face2顶点2的法向量
var n3 = new THREE.Vector3(0, 0, -1); //三角面3Face3顶点3的法向量
// 设置三角面Face3三个顶点的法向量
face1.vertexNormals.push(n1,n2,n3);
```
#### 2.定义三角形面的法线方向
```javascript
// 三角面2
var face2 = new THREE.Face3(0, 2, 3);
// 设置三角面法向量
face2.normal=new THREE.Vector3(0, -1, 0);

//三角面face1、face2添加到几何体中
geometry.faces.push(face1,face2);
```

## 三角形颜色
网格模型Mesh有效。。。。无效

```javascript
// 三角形1颜色
face1.color = new THREE.Color(0xffff00);

// 设置三角面face1三个顶点的颜色
face2.vertexColors = [
  new THREE.Color(0xffff00),
  new THREE.Color(0xff00ff),
  new THREE.Color(0x00ffff),
]

// 三角面(网格)渲染模式
var material = new THREE.MeshLambertMaterial({
  // color: 0xff00ff, //三角面颜色
	vertexColors:THREE.VertexColors,
  side: THREE.DoubleSide //两面可见
}); //材质对象
var mesh = new THREE.Mesh(geometry, material); //网格模型对象Mesh
scene.add(mesh)
```

## 练习
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>three.js入门</title>
		<style type="text/css">
			body{margin:0;overflow: hidden;}
		</style>
		<script src="http://www.yanhuangxueyuan.com/versions/threejsR92/build/three.js"></script>
		<script src="http://www.yanhuangxueyuan.com/threejs/examples/js/controls/OrbitControls.js"></script>
	</head>
	<body>
		<div id="window"></div>
		<script type="text/javascript">
			/* 创建场景对象 */
			var scene = new THREE.Scene()
		  var geometry = new THREE.Geometry();
			var p1 = new THREE.Vector3(0,0,0);
			var p2 = new THREE.Vector3(10,0,0);
			var p3 = new THREE.Vector3(10,10,0);
			var p4 = new THREE.Vector3(0,10,0);
			var p5 = new THREE.Vector3(10,0,10);
			var p6 = new THREE.Vector3(0,0,10);
			var p7 = new THREE.Vector3(0,10,10);
			var p8 = new THREE.Vector3(10,10,10);
			geometry.vertices.push(p1,p2,p3,p4,p5,p6,p7,p8)
			// 前面
			var face1 = new THREE.Face3(0,1,2);
			face1.normal=new THREE.Vector3(0,0,1)
			var face2 = new THREE.Face3(0,2,3);
			face2.normal=new THREE.Vector3(0,0,1)
			face1.color = new THREE.Color(0xff0000)
			face2.color = new THREE.Color(0xf00000)
			// 下面
			var face3 = new THREE.Face3(0,1,4);
			face3.normal=new THREE.Vector3(0,-1,0)
			var face4 = new THREE.Face3(0,4,5);
			face4.normal=new THREE.Vector3(0,-1,0)
			face3.color = new THREE.Color(0x00ff00)
			face4.color = new THREE.Color(0x00f000)
			// 左面
			var face5 = new THREE.Face3(0,5,6);
			face5.normal=new THREE.Vector3(-1,0,0)
			var face6 = new THREE.Face3(0,3,6);
			face6.normal=new THREE.Vector3(1,0,0)
			face5.color = new THREE.Color(0x0000ff)
			face6.color = new THREE.Color(0x0000f0)
			// 后面
			var face7 = new THREE.Face3(5,6,7);
			face7.normal=new THREE.Vector3(0,0,1)
			var face8 = new THREE.Face3(5,4,7);
			face8.normal=new THREE.Vector3(0,0,-1)
			face7.color = new THREE.Color(0xff00ff)
			face8.color = new THREE.Color(0xf000f0)
			// 右面
			var face9 = new THREE.Face3(1,2,7);
			face9.normal=new THREE.Vector3(1,0,0)
			var face10 = new THREE.Face3(1,4,7);
			face10.normal=new THREE.Vector3(1,0,0)
			face9.color = new THREE.Color(0xffff00)
			face10.color = new THREE.Color(0xf0f000)
			// 上面
			var face11 = new THREE.Face3(2,3,7);
			face11.normal=new THREE.Vector3(0,-1,0)
			var face12 = new THREE.Face3(3,6,7);
			face12.normal=new THREE.Vector3(0,-1,0)
			face11.color = new THREE.Color(0x00ffff)
			face12.color = new THREE.Color(0x00f0f0)

			geometry.faces.push(face1,face2,face3,face4,face5,face6,face7,face8,face9,face10,face11,face12)

			// 三角面(网格)渲染模式
			var material = new THREE.MeshLambertMaterial({
			  // color: 0x0000ff, //三角面颜色
				vertexColors:THREE.VertexColors,
			  side: THREE.DoubleSide //两面可见
			}); //材质对象

			var mesh = new THREE.Mesh(geometry, material); //网格模型对象Mesh
			scene.add(mesh)

			/* 设置光源 */
			// 环境光
			var ambient = new THREE.AmbientLight(0xeeeeee);
			scene.add(ambient);
			// 聚光灯、点光源
			var point = new THREE.PointLight(0xFFFFFF);
			point.position.set(200,200,200)
			scene.add(point);


			/* 设置相机 */
			var width = window.innerWidth,
			height = window.innerHeight,
			ratio = width / height,
			s = 20;	// 三维场景显示范围控制系数，系数越大，显示的范围越大
			// 创建相机
			var camera = new THREE.OrthographicCamera(-s * ratio,s*ratio,s,-s,1,1000);
			// 设置相机位置
			camera.position.set(200,300,200);
			// 设置相机方向(指向的场景对象)
			camera.lookAt(scene.position);


			/* 创建渲染器对象 */
			var renderer = new THREE.WebGLRenderer;
			// 设置渲染区域尺寸
			renderer.setSize(width,height);
			// 设置背景颜色
			renderer.setClearColor(0xb9d3ff,1);
			// 元素中插入canvas对象
			document.getElementById("window").appendChild(renderer.domElement);
			// 渲染（指定场景、相机作为参数）

			/* 创建坐标轴 */
			var axes = new THREE.AxesHelper(200);
			scene.add(axes)

			// 自动旋转
			// function render(){
			// 	renderer.render(scene,camera);
			// 	mesh.rotateY(0.01)
			// 	requestAnimationFrame(render);
			// }
			// render()

			function render(){
				renderer.render(scene,camera);
			}
			render();
			// 创建控件对象
			var controls = new THREE.OrbitControls(camera,renderer.domElement)
			// 监听鼠标键盘时间
			controls.addEventListener('change',render)
		</script>
	</body>
</html>

```

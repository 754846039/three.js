# 构建页面框架

--- 拷贝three.js源码src内容

```HTML
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<script text="module" charset="UTF-8" src="libs/three.js/Three.js"></script>
	<title>three.js</title>
	<style>
		body{margin:0;overflow: hidden;}
	</style>
</head>
<body>
	<div id="puidu-webgl-output"></div>
	<script type="module">
		import{REVISION}from "./libs/three.js/three.js"
		console.log(REVISION)
		console.log("当前three.js版本号：",window.__THREE__)
	</script>
</body>
</html>
```

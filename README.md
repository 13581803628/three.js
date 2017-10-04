three.js
========

[![Gitter][gitter-badge]][gitter-badge-url]
[![Latest NPM release][npm-badge]][npm-badge-url]
[![License][license-badge]][license-badge-url]
[![Dependencies][dependencies-badge]][dependencies-badge-url]
[![Dev Dependencies][devDependencies-badge]][devDependencies-badge-url]

#### JavaScript 3D 库 ####

此项目的目标是创建一个易用、轻量的3D库。这个库支持 &lt;canvas&gt;、&lt;svg&gt;、CSS3D 和 WebGL 渲染器。

[示例](http://threejs.org/examples/) &mdash;
[说明文档](http://threejs.org/docs/) &mdash;
[Wiki](https://github.com/mrdoob/three.js/wiki) &mdash;
[正在迁移](https://github.com/mrdoob/three.js/wiki/Migration-Guide) &mdash;
[帮助](http://stackoverflow.com/questions/tagged/three.js)

### 用法 ###

下载 [压缩库文件](http://threejs.org/build/three.min.js) 并将它包含在你的网页中。
另外，查看 [怎么自己构建这个库](https://github.com/mrdoob/three.js/wiki/Build-instructions)。

```html
<script src="js/three.min.js"></script>
```

下面的代码创建了一个场景、一个相机和一个几何立方体，并将这个几何空间放入场景中。然后，给这个场景和相机创建了一个 `WebGL` 渲染器，并在 document.body 中添加一个视窗。最后，用相机产生一个立方体随着场景的动画。

```javascript
var scene, camera, renderer;
var geometry, material, mesh;

init();
animate();

function init() {

	scene = new THREE.Scene();

	camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 1, 10000 );
	camera.position.z = 1000;

	geometry = new THREE.BoxGeometry( 200, 200, 200 );
	material = new THREE.MeshBasicMaterial( { color: 0xff0000, wireframe: true } );

	mesh = new THREE.Mesh( geometry, material );
	scene.add( mesh );

	renderer = new THREE.WebGLRenderer();
	renderer.setSize( window.innerWidth, window.innerHeight );

	document.body.appendChild( renderer.domElement );

}

function animate() {

	requestAnimationFrame( animate );

	mesh.rotation.x += 0.01;
	mesh.rotation.y += 0.02;

	renderer.render( scene, camera );

}
```

如果一切都运行良好的话你会看到 [这个画面](https://jsfiddle.net/hfj7gm6t/)。

### 更改日志 ###

[releases](https://github.com/mrdoob/three.js/releases)


[gitter-badge]: https://badges.gitter.im/mrdoob/three.js.svg
[gitter-badge-url]: https://gitter.im/mrdoob/three.js
[npm-badge]: https://img.shields.io/npm/v/three.svg
[npm-badge-url]: https://www.npmjs.com/package/three
[license-badge]: https://img.shields.io/npm/l/three.svg
[license-badge-url]: ./LICENSE
[dependencies-badge]: https://img.shields.io/david/mrdoob/three.js.svg
[dependencies-badge-url]: https://david-dm.org/mrdoob/three.js
[devDependencies-badge]: https://img.shields.io/david/dev/mrdoob/three.js.svg
[devDependencies-badge-url]: https://david-dm.org/mrdoob/three.js#info=devDependencies

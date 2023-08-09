<script setup>
import * as PIXI from "pixi.js";

// 创建应用
const app = new PIXI.Application({
  width: window.innerWidth,
  height: window.innerHeight,
  backgroundColor: 'lightblue',
  resolution: window.devicePixelRatio || 1,
  antialias: true,
});

// 挂载元素
document.body.appendChild(app.view);

// 创建一个矩形
const rect = new PIXI.Graphics();
// 设置边框样式
rect.lineStyle(1, 0xff0000, .5); // 线宽 颜色 透明度
rect.beginFill(0x66ccff, 0.8);
rect.drawRect(200, 200, 400, 400);
rect.endFill();

// 矩形的缩放
// rect.scale.set(1.25, 0.75);
// rect.scale.x = 0.5;
// rect.scale.y = 0.5;

// 矩形的位移
rect.position.set(300, 200)
// rect.position.x = -200;
// rect.position.y = -200;

// 矩形的旋转
rect.rotation = 0.5;

// 矩形的锚点
rect.pivot.set(200,200)

// 矩形添加到舞台
app.stage.addChild(rect);

// 创建一个圆形
const circle = new PIXI.Graphics();
circle.beginFill(0x66ccff)
circle.drawCircle(100, 100, 32);
circle.endFill();

app.stage.addChild(circle)

</script>

<template>
  <div></div>
</template>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
canvas {
  width: 100vw;
  height: 100vh;
  position: fixed;
  left: 0;
  right: 0;
}
</style>

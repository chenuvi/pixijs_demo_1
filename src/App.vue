<script setup>
import * as PIXI from "pixi.js";

// 创建应用
const app = new PIXI.Application({
  width: window.innerWidth,
  height: window.innerHeight,
  backgroundColor: 'lightblue',
  resolution: window.devicePixelRatio || 1,
});

// 挂载元素
document.body.appendChild(app.view);

// 创建一个矩形
const rect = new PIXI.Graphics();
rect.beginFill(0x66ccff);
rect.drawRect(200, 200, 400, 300);
rect.endFill();

// 矩形添加到舞台
app.stage.addChild(rect);


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

<script setup>
  import * as PIXI from "pixi.js"
  import ImgBunny from "./assets/bunny.png"

  // 创建应用
  const app = new PIXI.Application({
    width: window.innerWidth,
    height: window.innerHeight,
    backgroundColor: "lightblue",
    resolution: window.devicePixelRatio || 1,
  })

  // 挂载元素
  document.body.appendChild(app.view)

  // 创建一个纹理
  const texture = PIXI.Texture.from(ImgBunny)

  // 创建一个精灵
  const sprite = new PIXI.Sprite(texture)

  // 设置精灵位置
  sprite.x = app.screen.width / 2
  sprite.y = app.screen.height / 2

  // 精灵旋转 45度
  // sprite.rotation = Math.PI / 4;

  // ticker 实现动画
  const ticker = PIXI.Ticker.shared
  ticker.add((delta) => {
    sprite.rotation += 0.01 * delta
  })

  // 给精灵添加点击事件
  sprite.interactive = true
  sprite.on("click", () => {
    console.log("click")
  })

  // 精灵添加鼠标移入事件
  sprite.on("pointerenter", () => {
    console.log("pointerenter")
    sprite.alpha = 1
  })

  // 精灵添加鼠标移出事件
  sprite.on("pointerout", () => {
    console.log("pointerout")
    sprite.alpha = 0.5
  })

  app.stage.addChild(sprite)

  app.stage.addChild(sprite)

  // 绘制一个圆形
  const circle = new PIXI.Graphics()
  circle.beginFill(0x00ff00)
  circle.drawCircle(100, 100, 32)
  circle.endFill()

  // 给圆形添加点击事件
  circle.interactive = true
  circle.on("click", () => {
    console.log("circle click")
  })
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

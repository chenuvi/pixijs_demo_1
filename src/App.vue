<script setup>
  import * as PIXI from "pixi.js"
  // 本地图片转 URl
  function getImageUrl(name, suffix = png) {
    return new URL(`./assets/${name}.${suffix}`, import.meta.url).href
  }

  // 创建应用
  const app = new PIXI.Application({
    width: window.innerWidth,
    height: window.innerHeight,
    backgroundColor: "lightblue",
    resolution: window.devicePixelRatio || 1,
  })

  // 挂载元素
  document.body.appendChild(app.view)

  // 显示 hello world
  const text = new PIXI.Text("hello world", {
    fontFamily: "Arial",
    fontSize: 300,
    fill: "#000000",
    align: "center",
  })
  text.x = app.screen.width / 2
  text.y = app.screen.height / 2
  text.anchor.set(0.5)
  app.stage.addChild(text)

  // 创建一个精灵，并铺满整个屏幕
  const sprite = PIXI.Sprite.from(getImageUrl("Rick_And_Morty", "jpg"))
  sprite.width = app.screen.width
  sprite.height = app.screen.height

  // text 作为 sprite 的遮罩层
  // TODO sprite.mask = text
  text.mask = sprite


  app.stage.addChild(sprite)
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

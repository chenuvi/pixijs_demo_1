<script setup>
  import * as PIXI from "pixi.js"
  import { OutlineFilter, GlowFilter } from "pixi-filters"
  // 本地图片转 URl
  function getImageUrl(name, suffix = "png") {
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

  // 创建一个纹理
  const texture = PIXI.Texture.from(getImageUrl("bunny"))

  // 创建一个精灵
  const sprite = new PIXI.Sprite(texture)
  sprite.anchor.x = 0.5
  sprite.anchor.y = 0.5

  // 精灵放大两倍
  sprite.scale.x = 2
  sprite.scale.y = 2

  sprite.position.x = app.screen.width / 2
  sprite.position.y = app.screen.height / 2
  app.stage.addChild(sprite)

  // 创建模糊滤镜
  const blurFilter = new PIXI.BlurFilter()
  blurFilter.blur = 3

  // // 监听鼠标移入精灵
  // sprite.interactive = true
  // sprite.on("pointerover", () => {
  //   blurFilter.blur = 0
  // })

  // // 监听鼠标移出精灵
  // sprite.on("pointerout", () => {
  //   blurFilter.blur = 3
  // })

  // 创建轮廓滤镜
  const outlineFilter = new OutlineFilter(10, 0xffff00)
  // 创建发光过滤滤镜
  const glowFilter = new GlowFilter({
    color: 0xff0000,
    alpha: 0.5,
    distance: 15,
    quality: 0.5,
    outerStrength: 10,
  })
  glowFilter.color = 0xff0000
  glowFilter.alpha = 0.5
  sprite.filters = [outlineFilter, glowFilter]
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

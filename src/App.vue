<script setup>
  import * as PIXI from "pixi.js"

  // 本地图片转 URl
  function getImageUrl(name) {
    return new URL(`./assets/${name}.png`, import.meta.url).href
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

  // 添加创景1的资源
  PIXI.Assets.addBundle("scene1", {
    bunny: getImageUrl("bunny"),
    user: getImageUrl("user"),
    video: getImageUrl("video"),
  })
  const texturesPromise = PIXI.Assets.loadBundle("scene1", (progress) => {
    console.log("progress: ", progress)
    console.log("资源加载完毕")
  })

  // 添加图片资源
  // PIXI.Assets.add("bunny", getImageUrl("bunny"))
  // PIXI.Assets.add("user", getImageUrl("user"))
  // PIXI.Assets.add("video", getImageUrl("video"))

  // 异步加载资源
  // const texturesPromise = PIXI.Assets.load(["bunny", "user", "video"])

  texturesPromise.then((textures) => {
    // 创建一个容器
    const container = new PIXI.Container()

    const spriteBunny = new PIXI.Sprite(textures["bunny"])
    // 设置精灵位置
    spriteBunny.x = app.screen.width / 2
    spriteBunny.y = app.screen.height / 2
    // 缩放精灵
    container.addChild(spriteBunny)

    const spriteUser = new PIXI.Sprite(textures["user"])
    container.addChild(spriteUser)
    app.stage.addChild(container)
  })
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

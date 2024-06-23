<template><canvas id="live2d"></canvas></template>

<script lang="ts" setup>
import * as PIXI from 'pixi.js'
import { Live2DModel } from 'pixi-live2d-display'
import { onMounted, reactive, ref } from 'vue'

window.PIXI = PIXI

const live2d = ref<HTMLElement>()
console.log(live2d.value)

onMounted(() => {
  const app = new PIXI.Application({
    view: live2d.value,
    width: 800,
    height: 800,
    autoStart: true,
    backgroundAlpha: 1
  })

  ;(async () => {
    const scale = 0.5

    const model = await Live2DModel.from('model/凯尔希live2d/凯尔希直播版1.model3.json')
    model.scale.set(scale, scale)
    model.anchor.set(0.5, 0.5)
    app.stage.addChild(model)
  })()
})
</script>

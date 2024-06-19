<script setup lang="ts">
import { ref } from 'vue'

const bg = ref<HTMLElement>()
function bgmove(e: MouseEvent) {
  const w = document.body.clientWidth
  const h = document.body.clientHeight
  
  bg.value!.style.backgroundPositionX = 0.05 * (e.x - w / 2) + 'px'
  bg.value!.style.backgroundPositionY = 0.02 * (e.y - h / 2) + 'px'
}
</script>

<template>
  <main @mousemove="bgmove" ref="bg"></main>
</template>

<style>
main {
  height: 100vh;
  background: url(../assets/bg.png) no-repeat center/80%;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>



<template>
  <main @mousemove="bgmove" ref="bg"></main>
  <button @click="togglebgm" class="playmusic">play</button>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { NButton } from 'naive-ui'

const bg = ref<HTMLElement>()

function bgmove(e: MouseEvent) {
  const w = document.body.clientWidth
  const h = document.body.clientHeight

  bg.value!.style.backgroundPositionX = 0.05 * (e.x - w / 2) + 'px'
  bg.value!.style.backgroundPositionY = 0.02 * (e.y - h / 2) + 'px'
}
</script>

<script lang="ts">
const bgm = new Audio("src/assets/BGM00.OGG")
const togglebgm = () => {
  if(bgm.paused) {
    bgm.play()
    bgm.volume = 0
    const id = setInterval(()=>{
      bgm.volume+=0.01;
      console.log(bgm.volume);
      
      bgm.volume >= 0.99 ? clearInterval(id) : null
    }, 10)
  } else {
    bgm.volume = 0.99
    const id = setInterval(()=>{
      bgm.volume-=0.01;
      console.log(bgm.volume);
      
      if(bgm.volume <= 0.01) {
        clearInterval(id)
        bgm.pause()
      }
    }, 10)
  }
}
</script>

<style>
main {
  height: 100vh;
  background: url(../assets/bg.png) no-repeat center/80%;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
}

.playmusic {
  position: absolute;
  width: 4em;
  height: 4em;
  right: 2em;
  bottom: 2em;
  font-family: 'Courier New', Courier, monospace;
  font-weight: 2000;
  border-radius: 1em;
  border: 0.1em black solid
}
.playmusic:hover {
  scale: 1.03
}
</style>



<template>
  <main @mousemove="bgmove" ref="bg"></main>
  <!-- <button @click="togglebgm" class="playmusic">play</button> -->
  <PlayButtom @click="togglebgm" class="playmusic"></PlayButtom>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { NButton } from 'naive-ui'
import PlayButtom from '@/components/PlayButtom.vue'
import { startSakura } from '@/components/SakuraFalling.vue'

const bg = ref<HTMLElement>()

function bgmove(e: MouseEvent) {
  const w = document.body.clientWidth
  const h = document.body.clientHeight

  bg.value!.style.backgroundPositionX = 0.05 * (e.x - w / 2) + 'px'
  bg.value!.style.backgroundPositionY = 0.02 * (e.y - h / 2) + 'px'
}

startSakura();
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

<style lang="scss">
$scale: 0.6;
main {
  height: 100vh;
  background: url(../assets/bg.png) no-repeat center/80%;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: background-position linear 0.1s
}

.playmusic {
  position: absolute;
  right: 2em;
  bottom: 2em;
  scale: $scale;
  transition: scale .1s linear;
}
.playmusic:hover {
  scale: $scale+0.04;
}
</style>

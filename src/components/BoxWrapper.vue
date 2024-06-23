<template>
  <div class="wrapper">
    <Box v-for="item in data.data" :key="item.id">
      <template v-slot:title>{{ item.title }}</template>
      <template v-if="item.icon" v-slot:icon><Icon /></template>
      <template v-slot:text>{{ item.text }}</template>
    </Box>
  </div>
</template>

<script setup lang="ts">
import Box from '@/components/Box.vue'
import Icon from '@/components/Icon.vue'
import { defineProps } from 'vue'
const data = defineProps(['data'])
</script>

<style scoped>
.wrapper {
  display: flex;
  width: 100%;
  overflow: auto;
  height: 100%;
}
</style>

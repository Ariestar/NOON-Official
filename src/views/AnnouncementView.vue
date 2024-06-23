<template>
  <Layout>
    <template #header>
      <div class="header">公告 | Announcements</div>
    </template>
    <template #left>
      <div class="title">公告</div>
    </template>
    <template #mid>
      <BoxWrapper :data="announcements" />
    </template>
  </Layout>
</template>

<script setup lang="ts">
import Layout from '@/components/Layout.vue'
import BoxWrapper from '@/components/BoxWrapper.vue'

const announcements = [
  {
    id: 1,
    title: '123',
    text: 'haha'
  },
  {
    id: 2,
    title: '2',
    text: '2'
  }
]
</script>

<style scoped>

.header {

}
</style>

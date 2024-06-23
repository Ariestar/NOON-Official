<template>
  <div class="block">
    <slot name="title"></slot>
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>

<script setup lang="ts">
</script>

<style lang="scss" scoped>
.block {
  position: relative;
  width: 100%;
  height: 3em;
  border-radius: 10px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
  overflow: hidden;
  margin: 1em;
  padding: 0 1em;
}
</style>

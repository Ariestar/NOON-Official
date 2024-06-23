<template>
  <div class="container">
    <header class="header">
      <slot name="header"></slot>
    </header>
    <main class="main">
      <div class="left">
        <slot name="left"></slot>
      </div>
      <div class="mid">
        <slot name="mid"></slot>
      </div>
      <div class="right">
        <slot name="right"></slot>
      </div>
    </main>
    <footer class="footer">
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
$aside-width: 12em;
$head-height: 5em;
$padding: 0.5em;
.container {
  $padding: 1em;
  position: fixed;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
}
.header {
  height: $head-height;
  width: 100%;
  position: sticky;
  padding: 0.5em;
  background-color: red;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.5);
}
.main {
  bottom: 0;
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: row;
  background-color: aquamarine;
  justify-content: space-between;
}
.left {
  width: $aside-width;
  padding: 0.5em;
  background-color: green;
}
.mid {
  padding: 0.5em;
  width: 100%;
}
.right {
  width: $aside-width;
  padding: 0.5em;
  background-color: blue;
}
</style>

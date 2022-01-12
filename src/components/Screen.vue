<template>
  <div class="screen" :style="{background: background, color: color}">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "Screen",
  props: [ "background", "color" ]
}
</script>

<style>
.screen {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  text-align: center;
}

.screen > p {
  font-size: 2rem;
  max-width: 30ch;
}
</style>
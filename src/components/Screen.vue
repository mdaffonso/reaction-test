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
  padding: 2rem 1rem;
}

.screen > p {
  font-size: clamp(1.25rem, 7.5vw, 2.5rem);
  max-width: 30ch;
}
</style>
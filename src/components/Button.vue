<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button"
}
</script>

<style scoped>
button {
  padding: 1rem 3rem;
  margin: 3rem 0;
  border-radius: 100rem;
  border: none;
  color: black;
  background: white;
  font-size: 1.5rem;
}
</style>
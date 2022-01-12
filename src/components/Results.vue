<template>
  <Screen background="black" color="white">
    <p>Você reagiu em</p>
    <p class="reaction">{{ time }}</p>
    <p>milissegundos!</p>
    <p class="category">{{ category }}</p>
    <Button @click="replay">de novo</Button>
  </Screen>
</template>

<script>
import Screen from "./Screen.vue"
import Button from "./Button.vue"
export default {
  name: "Results",
  components: { Screen, Button },
  props: [
    "time",
    "replay"
  ],

  data () {
    return {
      category: null
    }
  },

  mounted () {
    if (this.time < 200) {
      this.category = "Relâmpago Marquinhos"
    } else if (this.time < 285) {
      this.category = "Ser Humano"
    } else if (this.time < 450) {
      this.category = "Meio Lento"
    } else {
      this.category = "Lesmão"
    }
  }
}
</script>

<style scoped>
p {
  text-transform: uppercase;
}

.reaction {
  font-size: clamp(1.75rem, 8vw, 3.5rem);
  color: aquamarine;
}

.category {
  font-size: clamp(2rem, 9vw, 5rem);
  margin: 3rem 0;
}
</style>
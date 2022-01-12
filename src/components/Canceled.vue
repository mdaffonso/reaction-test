<template>
  <Screen background="crimson" color="white">
    <p>Você clicou cedo demais :(</p>
    <Button @click="replay">de novo</Button>
  </Screen>
</template>

<script>
import Screen from "./Screen.vue"
import Button from "./Button.vue"
export default {
  name: "Canceled",
  components: { Screen, Button },
  props: ["replay"]
}
</script>
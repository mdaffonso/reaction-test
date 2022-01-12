<template>
  <Screen background="#ecd500" color="black" v-if="isPlaying" @click="cancel">
    <p>Quando a tela mudar de cor, clique o mais rápido que conseguir!</p>
  </Screen>
</template>

<script>
import Screen from "./Screen.vue"
export default {
  name: "Playing",
  components: { Screen },
  props: [ "isPlaying" ],
  methods: {
    cancel () {
      this.$emit("cancel")
    }
  }
}
</script>
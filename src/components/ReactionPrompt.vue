<template>
  <Screen background="#2dc000" color="white" class="prompt" @click="stopTimer" v-if="show">
    <h2>Clique agora!</h2>
  </Screen>
</template>

<script>
import Screen from "./Screen.vue"
export default {
  name: "ReactionPrompt",
  
  components: { Screen },

  props: [
    "delay"
  ],

  data () {
    return {
      show: false,
      timer: null,
      reactionTime: 0
    }
  },

  mounted () {
    setTimeout(() => {
      this.show = true
      this.startTimer()
    }, this.delay)
  },

  methods: {
    startTimer () {
      this.timer = setInterval(() => {
        this.reactionTime += 3
      }, 3)
    },

    stopTimer () {
      clearInterval(this.timer)
      this.show = false
      this.$emit("react", this.reactionTime)
      this.reactionTime = 0
    }
  }
}
</script>

<style scoped>
.prompt {
  z-index: 100;
}

h2 {
  font-size: clamp(1.75rem, 8vw, 4rem);
  text-align: center;
}
</style>
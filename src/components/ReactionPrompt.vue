<template>
  <div class="prompt" @click="stopTimer" v-if="show">
    <h2>Clique agora!</h2>
  </div>  
</template>

<script>
export default {
  name: "ReactionPrompt",
  
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
  display: flex;
  justify-content: center;
  align-items: center;

  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  color: white;
  background: rgb(45, 192, 0);

  z-index: 100;
}

.prompt h2 {
  font-size: 3rem;
}
</style>
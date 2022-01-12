<template>
  <ReactionPrompt v-if="isPlaying" :delay="delay" @react="handleReaction" />
  
  <Playing v-if="isPlaying" :isPlaying="isPlaying" @cancel="handleCancel" />

  <Screen background="#3c69e4" color="white" @click="start" v-else>
    <h1>Reaction Test</h1>
    <p>Clique em qualquer lugar para iniciar.</p>
  </Screen>

  <Results v-if="reactionTime !== null && !canceled" :time="reactionTime" :replay="start" />

  <Canceled v-if="canceled" :replay="start" />
</template>

<script>
import Screen from "./components/Screen.vue"
import ReactionPrompt from "./components/ReactionPrompt.vue"
import Playing from "./components/Playing.vue"
import Results from "./components/Results.vue"
import Canceled from "./components/Canceled.vue"

export default {
  name: 'App',

  components: {
    Screen,
    ReactionPrompt,
    Playing,
    Results,
    Canceled
  },

  data () {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null,
      canceled: false
    }
  },

  methods: {
    start () {
      this.delay = 2000 + Math.random() * 8000
      this.isPlaying = true
      this.reactionTime = null
      this.canceled = false
    },

    handleReaction (rt) {
      this.reactionTime = rt
      this.isPlaying = false
      this.delay = null
    },

    handleCancel () {
      this.isPlaying = false
      this.delay = null
      this.canceled = true
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 3rem;
  margin-bottom: 2em;
  padding: 0 0 0.25em 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.3);
}
</style>

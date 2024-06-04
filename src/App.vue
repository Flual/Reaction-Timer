<template>
  <h1>Reaction Timer</h1>
  <!-- Button Startet das Spiel und is deaktiviert während das Spiel läuft -->
  <button @click="start" :disabled="isPlaying">Play</button>

  <!-- Reaktionsblock wenn geklickt Spiel vorbei -->
  <block v-if="isPlaying" :delay="delay" @end="endGame"/>

  <p v-if="showResult">Reaction time : {{ score }} ms</p>
</template>

<script>
import block from './components/block.vue'

export default {
  name: 'App',
  components: { block },
  // Fnktion idled das Spiel und gibt den Delay einen Anfangswert
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    // Die Funktion startet einen Timer und startet das Spiel
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>

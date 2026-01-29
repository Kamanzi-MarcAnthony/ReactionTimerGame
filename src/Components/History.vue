<template>
  <div>
    <h3>
      Best Score
    </h3>
    <p v-if="score == null">
        No previous scores recorded.
    </p>
    <p v-if="score != null" class="best-score">
        Your best score is {{ bestScore }} ms
    </p>
  </div>
</template>

<script>
export default {
    props: ['score', 'isplaying'],
    
    data() {
        return {
        bestScore: null
        }
    },

    watch: {
    score(newScore) {
      if (newScore === null) return

      // First score ever
      if (this.bestScore === null) {
        this.bestScore = newScore
        return
      }
      // Reaction timer logic: lower is better
      if (newScore < this.bestScore) {
        this.bestScore = newScore
      }
    }
  }
}
</script>

<style scoped>
    
</style>
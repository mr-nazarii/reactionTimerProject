<script>
import BlockElement from "./components/BlockElement.vue";
import ResultsComponent from "./components/ResultsComponent.vue";
export default {
  data() {
    return {
      active: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.active = true;
      this.delay = 2000 + Math.random() * 5000;
      this.score = null;
      console.log(this.delay);
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.active = false;
    },
  },
  components: { BlockElement, ResultsComponent },
};
</script>

<template>
  <div class="wrapper">
    <h1>Reaction <span>Timer</span></h1>
  </div>
  <div class="wrapper">
    <button @click="start" :disabled="active">Play</button>
  </div>
  <BlockElement v-if="active" :delay="delay" @end="endGame" />
  <ResultsComponent v-if="score !== null" :score="score" />
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}
span {
  color: hsla(160, 100%, 37%, 1);
}

button {
  padding: 10px 30px;
  background-color: hsla(160, 100%, 37%, 1);
  border: none;
  border-radius: 20px;
  font-weight: 700;
  color: white;
  text-transform: uppercase;
}

button:disabled {
  background-color: rgb(132, 182, 165);
}
</style>

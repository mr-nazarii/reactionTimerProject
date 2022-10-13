<template>
  <div @click="stopTimer" class="block" v-if="showBlock">click me</div>
</template>
<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>
<style>
.block {
  width: 300px;
  height: 200px;
  background-color: hsla(160, 100%, 37%, 1);
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 40px auto;
  border-radius: 20px;
  font-weight: 600;
  color: white;
  text-transform: uppercase;
}
</style>

<template>
  <div>
    <p>Result: {{ score }} ms</p>
    <p>{{ rank }}</p>
  </div>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: "",
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Godlike fingers";
    } else if (this.score < 400) {
      this.rank = "Not bad";
    } else {
      this.rank = "Too slow";
    }
  },
};
</script>
<style>
p {
  text-align: center;
  font-size: 20px;
}
</style>

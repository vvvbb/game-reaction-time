<template>
  <p>Reaction time : {{ score }} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Fast";
    } else if (this.score < 400) {
      this.rank = "On a way";
    } else {
      this.rank = "Quiet..";
    }
  },
};
</script>

<style>
.rank{
    font-size: 1.4rem;
    color: crimson;
    font-weight: bold;
}
</style>

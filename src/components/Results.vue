<template>
  <p>
    Reaction time : <span>{{ score }} ms</span>
  </p>
  <p class="rank">{{ rank }}</p>
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
      this.rank = "Wow fast as lightning !!";
    } else if (this.score < 400) {
      this.rank = "On your way to be better";
    } else {
      this.rank = "Quiet..";
    }
  },
};
</script>

<style>
.rank {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  font-size: 1.4rem;
  color: #008f18;
  font-weight: bold;
}
p span {
  text-decoration: underline;
}
</style>

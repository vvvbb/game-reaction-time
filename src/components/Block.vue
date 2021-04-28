<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
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
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      // console.log(this.delay)
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
    //   console.log(this.reactionTime);
    this.$emit('end',this.reactionTime) //emit second parameter to parent
    },
  },
};
</script>

<style>
.block {
    font-weight : bold;
    font-size: 2rem;
  width: 400px;
  border-radius: 20px;
  background: crimson;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>

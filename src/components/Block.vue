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
    // console.log("component mounted");
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
      this.$emit("end", this.reactionTime); //emit second parameter to parent
    },
  },
};
</script>

<style>
.block {
  display: flex;
  justify-content: center;
  align-items: center;
  
  width: 80%;
  height: 60%;
  margin: auto;
  border-radius: 2rem;

  font-size: 2rem;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;

  color: white;
  background: hsl(130, 83%, 67%);

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>

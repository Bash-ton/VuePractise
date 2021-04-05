<template>
  <div class="blockWrapper" @click="clickPermissions">
    <div v-if="showBlock" class="block" @click="stopTimer">click me!</div>
  </div>
</template>

<script>
export default {
  name: "Blocks",
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      time: null,
      reactionTimer: 0,
    };
  },
  mounted() {
    console.log("component has mounted");

    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTimer += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end-game", this.reactionTimer);
    },
    clickPermissions() {
        if(!this.showBlock){
            clearInterval(this.timer);
            this.$emit("end-game", "cheat");
        }
        
    },
  },
};
</script>


<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}

.blockWrapper {
    height: 100vh;
}
</style>

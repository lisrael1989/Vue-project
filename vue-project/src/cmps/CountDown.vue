<template>
  <section class="count-down">
    <h1 :class="{ 'red-text': timeLeft <= 6 && timeLeft > 0 }">{{ displayTime }}</h1>
  </section>

  <button class="restart-btn" @click="restartCountdown">Restart</button>
</template>

<script>
export default {
  data() {
    return {
      initialTime: 10,
      timeLeft: 10,
      intervalId: null,
    }
  },
  computed: {
    displayTime() {
      return this.timeLeft > 0 ? this.timeLeft : "0"
    },
  },
  mounted() {
    this.startCountdown()
  },
  beforeDestroy() {
    clearInterval(this.intervalId)
  },
  methods: {
    startCountdown() {
      this.intervalId = setInterval(() => {
        if (this.timeLeft > 0) {
          this.timeLeft -= 1
        } else {
          clearInterval(this.intervalId)
          this.handleDone()
        }
      }, 1000)
    },
    handleDone() {
      console.log("Done!")
    },
    restartCountdown() {
      clearInterval(this.intervalId)
      this.timeLeft = this.initialTime
      this.startCountdown()
    },
  },
}
</script>

<style lang="scss">
.count-down {
  display: flex;
  align-items: center;
  justify-content: center;

  margin: 30px auto;
  width: 150px;
  background-color: #e5e1e1;
  box-shadow: 1px 5px 10px rgba(104, 95, 95, 0.507);
  border-radius: 8px;

  h1 {
    margin: 5px;
    padding: 5px;
    color: #333;

    &.red-text {
      color: red;
    }
  }
}

.restart-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px auto;
  background-color: lightcoral;
  color: white;
  border: none;
  border: 1px solid lightgray;
  border-radius: 7px;
  width: 70px;
  height: 30px;
  cursor: pointer;

  &:hover {
    background: lightblue;
    color: black;
  }
}
</style>

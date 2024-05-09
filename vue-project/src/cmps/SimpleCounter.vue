<template>
  <section class="simple-counter">
    <button :disabled="counter <= 0" @click="ChangeVal(-1)">-</button>
    <span :class="counterStyle">{{ counter }}</span>
    <button :disabled="counter >= 10" @click="ChangeVal(1)">+</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      counter: 3,
    }
  },
  methods: {
    ChangeVal(diff) {
      this.counter += diff
    },
  },
  computed: {
    counterStyle() {
      return {
        low: this.counter < 3,
        high: this.counter > 7,
        odd: this.counter % 2,
      }
    },
  },
}
</script>

<style lang="scss">
.simple-counter {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 10px;
  width: fit-content;

  margin: 30px auto;
  width: 100px;
  background-color: #e5e1e1;
  box-shadow: 1px 5px 10px rgba(104, 95, 95, 0.507);
  border-radius: 8px;

  .low {
    color: red;
  }
  .high {
    color: green;
  }

  .odd {
    color: goldenrod;
    rotate: -25deg;
  }
}
</style>

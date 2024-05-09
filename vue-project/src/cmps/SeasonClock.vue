<template>
  <section class="season-clock" @click="toggleDark()" :class="{ light: !isDark, dark: isDark }">
    <h1>{{ calcMonth }} ({{ calcSeason }})</h1>
    <img :src="`src/seasons/${calcSeason}.png`" alt="" />
    <h1>{{ calcDay }}</h1>
    <h1 class="currentTime">{{ this.currentTime }}</h1>
  </section>
</template>

<script>
export default {
  data() {
    return {
      currDate: new Date(),
      isDark: false,
      currentTime: "",
      // intervalId: null,
    }
  },
  methods: {
    toggleDark() {
      this.isDark = !this.isDark
    },
    updateClock() {
      const now = new Date()
      const hours = String(now.getHours()).padStart(2, "0")
      const minutes = String(now.getMinutes()).padStart(2, "0")
      const seconds = String(now.getSeconds()).padStart(2, "0")
      this.currentTime = `${hours}:${minutes}:${seconds}`
    },
  },
  computed: {
    calcSeason() {
      const month = this.currDate.getMonth() + 1
      const day = this.currDate.getDay()
      let season
      switch (true) {
        case month >= 2 && month <= 4:
          season = "Spring"
          break
        case month >= 5 && month <= 7:
          season = "Summer"
          break
        case month >= 8 && month <= 10:
          season = "Autumn"
          break
        default:
          season = "Winter"
      }
      return season
    },
    calcDay() {
      const dayNames = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ]
      return dayNames[this.currDate.getDay()]
    },
    calcMonth() {
      const monthNames = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ]
      return monthNames[this.currDate.getMonth()]
    },
  },
  mounted() {
    this.updateClock()
    this.intervalId = setInterval(() => {
      this.currDate = new Date()
      this.updateClock()
    }, 1000)
  },
  beforeDestroy() {
    clearInterval(this.intervalId)
  },
}
</script>

<style lang="scss">
.season-clock {
  width: 300px;
  text-align: center;
  margin: 0 auto;
  border: 1px solid rgb(210, 206, 206);
  margin-bottom: 10px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);

  &.light {
    background: lightblue;

    & .currentTime {
      color: black;
    }
  }

  &.dark {
    background: rgb(37, 29, 179);
    color: white;
  }

  & .currentTime {
    border-top: 1px solid white;
    color: white;
  }
}
</style>

<script>
import SimpleCounter from "./cmps/SimpleCounter.vue"
import AnimalList from "./cmps/AnimalList.vue"
import SeasonClock from "./cmps/SeasonClock.vue"
import CountDown from "./cmps/CountDown.vue"
import Watchers from "./cmps/Watchers.vue"

export default {
  data() {
    return {
      route: "Watchers",
    }
  },
  components: {
    SimpleCounter,
    SeasonClock,
    AnimalList,
    CountDown,
    Watchers,
  },
}
</script>

<template>
  <header>
    <button @click="route = 'AnimalList'">Animal List</button>
    <button @click="route = 'SeasonClock'">Season Clock</button>
    <button @click="route = 'CountDown'">Count Down</button>
    <button @click="route = 'SimpleCounter'">Simple Counter</button>
    <button @click="route = 'Watchers'">Watchers</button>
  </header>

  <main>
    <AnimalList v-if="route === 'AnimalList'" />
    <SeasonClock v-if="route === 'SeasonClock'" />
    <CountDown v-if="route === 'CountDown'" />
    <SimpleCounter v-if="route === 'SimpleCounter'" />
    <Watchers v-if="route === 'Watchers'" />
  </main>
</template>

<style lang="scss">
main {
  margin-top: 20px;
}

header {
  line-height: 1.5;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;

  button {
    cursor: pointer;
    background-color: black;
    color: white;
    border-radius: 8px;
    height: 30px;

    &:hover {
      background-color: rgb(70, 189, 216);
      color: white;
      border: none;
    }
  }
}
</style>

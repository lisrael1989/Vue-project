<script>
import SimpleCounter from "./cmps/SimpleCounter.vue"
import AnimalList from "./cmps/AnimalList.vue"
import SeasonClock from "./cmps/SeasonClock.vue"
import CountDown from "./cmps/CountDown.vue"

export default {
  components: {
    SimpleCounter,
    SeasonClock,
    AnimalList,
    CountDown,
  },
  data() {
    return {
      route: "AnimalList",
    }
  },
}
</script>

<template>
  <header>
    <button @click="route = 'AnimalList'">Animal List</button>
    <button @click="route = 'SeasonClock'">Season Clock</button>
    <button @click="route = 'CountDown'">Count Down</button>
    <button @click="route = 'SimpleCounter'">Simple Counter</button>
  </header>

  <main>
    <AnimalList v-if="route === 'AnimalList'" />
    <SeasonClock v-if="route === 'SeasonClock'" />
    <CountDown v-if="route === 'CountDown'" />
    <SimpleCounter v-if="route === 'SimpleCounter'" />
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
  padding: 10px;

  button {
    &:hover {
      background-color: rgb(70, 189, 216);
      color: white;
    }
  }
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

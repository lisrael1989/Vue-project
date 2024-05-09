<script>
export default {
  props: ["watcher"],
  data() {
    return {}
  },
  methods: {
    onCloseModal() {
      this.$emit("closeModal")
    },
  },
}
</script>

<template>
  <div className="watcher-modal">
    <h3>{{ watcher.fullName }}</h3>
    <ul>
      <li v-for="(movie, idx) in watcher.movies" :key="{ idx }">{{ movie }}</li>
    </ul>

    <button @click="$emit('close')">Close</button>
  </div>
</template>

<style lang="scss" scoped>
.watcher-modal {
  position: absolute;
  inset: 0 0 auto auto;
  padding: 20px;
  background-color: lightcoral;
  box-shadow: 3px 5px 10px rgba(0, 0, 0, 0.434);
  min-width: 150px;

  h3 {
    text-align: center;
    font-size: 20px;
    margin-block-end: 10px;
    background-color: white;
  }

  ul {
    margin: 0;
    padding: 0;
    margin-block-end: 10px;
    padding: 10px;
    color: white;
  }

  button {
    cursor: pointer;
    background-color: #333;
    color: whitesmoke;
    border: none;
    padding: 5px;

    &:hover {
      background-color: whitesmoke;
      border: none;
      color: #333;
    }
  }
}
</style>

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

  h3 {
    text-align: center;
    font-size: 20px;
    margin-block-end: 10px;
  }

  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    margin-block-end: 10px;
  }
}
</style>

<script>
export default {
  props: ["watcher"],
  methods: {
    onRemoveWatcher() {
      this.$emit("remove", this.watcher._id)
    },
  },
}
</script>

<template>
  <article class="watcher-preview">
    <img :src="`src/${watcher.imgUrl}`" alt="Avatar picture" />
    <p>
      {{ watcher.fullName }}
    </p>
    <button class="btn-delete" @click.stop="onRemoveWatcher">X</button>
  </article>
</template>

<style lang="scss" scoped>
.watcher-preview {
  display: flex;
  position: relative;
  flex-direction: column;
  align-items: center;

  padding: 20px;
  background-color: #333;
  color: wheat;
  cursor: pointer;
  border-radius: 8px;

  img {
    max-width: 100%;
  }

  p {
    font-size: 24px;
    font-weight: 600;
    padding-top: 10px;
  }

  .btn-delete {
    cursor: pointer;
    position: absolute;
    top: -10px;
    left: -10px;
    border-radius: 50%;
    padding: 4px 8px;
  }
}
</style>

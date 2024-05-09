<script>
export default {
  props: ['watcher'],
  methods: {
    onRemoveWatcher() {
      this.$emit('remove', this.watcher._id)
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
  flex-direction: column;
  align-items: center;

  padding: 20px;
  background-color: lightgray;
  cursor: pointer;

  img {
    max-width: 100%;
  }

  p {
    font-size: 24px;
  }

  .btn-delete {
    cursor: pointer;
  }
}
</style>

<script>
import WatcherPreview from './WatcherPreview.vue'

export default {
  components: { WatcherPreview },
  props: ['watchers'],
  methods: {
    onWatcherRemoved(ev) {
      this.$emit('remove', ev)
    },
    onSelectWatcher(watcher) {
        this.$emit('selected', watcher)
    }
  },
}
</script>

<template>
  <ul class="watcher-list">
    <li @click="onSelectWatcher(watcher)" v-for="watcher in watchers" :key="watcher._id">
      <WatcherPreview
        :watcher="watcher"
        @remove="onWatcherRemoved"
        @click="() => onSelectWatcher(watcher)"
      />
    </li>
  </ul>
</template>

<style lang="scss" scoped>
.watcher-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;

  margin: 20px;
  padding: 0;
  list-style-type: none;
}
</style>

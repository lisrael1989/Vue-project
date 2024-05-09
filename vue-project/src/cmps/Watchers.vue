<script>
import { utilService } from "../services/util.service.js"

import WatcherList from "./WatcherList.vue"
import WatcherModal from "./WatcherModal.vue"

export default {
  components: { WatcherList, WatcherModal },
  data() {
    return {
      watchers: null,
      selectedWatcher: null,
    }
  },
  methods: {
    onAddWatcher() {
      const fullName = prompt("Enter full name")
      if (!fullName) return alert("Invalid name")

      const watcherToSave = {
        _id: utilService.makeId(),
        fullName,
        imgUrl: this.getRndImg(),
      }
      this.watchers.unshift(watcherToSave)
    },

    onRemoveWatcher(watcherId) {
      const watcherIdx = this.watchers.findIndex((w) => w._id === watcherId)
      if (watcherId < 0) return alert("Invalid watcher ID")
      this.watchers.splice(watcherIdx, 1)
    },

    onSelectWatcher(watcher) {
      this.selectedWatcher = watcher
    },

    getRndImg() {
      const imgUrls = [
        "src/avatars/avatar1.png",
        " src/avatars/avatar2.png",
        " src/avatars/avatar3.png",
        " src/avatars/avatar4.png",
        " src/avatars/avatar5.png",
      ]

      return imgUrls[this.getRandomInt(0, imgUrls.length)]
    },

    getRandomInt(min, max) {
      min = Math.ceil(min)
      max = Math.floor(max)
      return Math.floor(Math.random() * (max - min) + min)
    },
  },
  created() {
    this.watchers = [
      {
        _id: "u101",
        fullName: "Jasmin",
        imgUrl: "avatars/avatar1.png",
        movies: ["IronMan", "SpiderMan"],
      },
      {
        _id: "u102",
        fullName: "Loli",
        imgUrl: "avatars/avatar2.png",
        movies: ["Thor", "Hulk"],
      },
      {
        _id: "u103",
        fullName: "Ali",
        imgUrl: "avatars/avatar3.png",
        movies: ["Captain America", "AntMan"],
      },
      {
        _id: "u104",
        fullName: "Yan",
        imgUrl: "avatars/avatar4.png",
        movies: ["Black Panther", "The Avengers"],
      },
      {
        _id: "u105",
        fullName: "Israel",
        imgUrl: "avatars/avatar5.png",
        movies: ["Dr. Strange", "Marvels"],
      },
    ]
  },
}
</script>

<template>
  <section class="watcher-app">
    <h1>Watcher App</h1>

    <section class="watcher-index">
      <button class="btn-add" @click="onAddWatcher">Add user</button>
      <WatcherList @selected="onSelectWatcher" :watchers="watchers" @remove="onRemoveWatcher" />
    </section>

    <WatcherModal
      v-if="selectedWatcher"
      :watcher="selectedWatcher"
      @close="selectedWatcher = null"
    />
  </section>
</template>

<style lang="scss" scoped>
.watcher-app {
  h1 {
    margin-block-start: 15px;
    font-size: 32px;
    text-align: center;
  }

  .watcher-index {
    .btn-add {
      cursor: pointer;
      margin-inline-start: 20px;
    }
  }
}
</style>

<template>
  <p>view: <span @click="changeView('list')" :class="view === 'list' ? 'selected' : ''">list</span> / <span @click="changeView('grid')" :class="view === 'grid' ? 'selected' : ''">grid</span></p>
  <div v-if="view === 'list'">
    <ListItem v-for="album in albumList" :key="album.position" :album="album" />
  </div>
<div v-if="view === 'grid'" class="grid">
  <AlbumCard v-for="album in albumList" :key="album.position" :album="album" />
  </div>
</template>

<script>
import { ref } from "vue"
import { albums } from './albums'

import AlbumCard from './components/AlbumCard.vue'
import ListItem from './components/ListItem.vue'

export default {
  name: 'App',
  components: {
    AlbumCard,
    ListItem,
  },
  setup() {
    const albumList = albums;
    // console.log(albumList)
    return {
      albumList,
      view,
      changeView,
    }
  }
}

// let view = 'list';
let view = ref('grid')

function changeView(viewChoice) {
  view.value = viewChoice;
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.selected {
  font-weight: bold;
}
</style>

<style scoped>
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, 200px);
    grid-gap: 10px;
}
</style>
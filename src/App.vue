<template>
<div class="grid">
  <AlbumCard v-for="album in albumList" :key="album.position" :album="album" />
  </div>
</template>

<script>
import { albums } from './albums'

import AlbumCard from './components/AlbumCard.vue'

export default {
  name: 'App',
  components: {
    AlbumCard
  },
  setup() {
    const albumList = albums;
    // console.log(albumList)
    return {
      albumList,
    }
  }
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
</style>

<style scoped>
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, 200px);
    grid-gap: 10px;
}
</style>
<template>
    <input
      type="text"
      v-model="filterString"
      placeholder="Search Artist / Album title..."
    >
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
  data() {
    const fullAlbumList = albums;
    const albumList = fullAlbumList;
    
    return {
      albumList,
      fullAlbumList,
      filterString,
      view,
      changeView,
    }
  },
    watch: {
      filterString: function() {
          let shortlist = this.fullAlbumList.filter(album => {
            return album.artist.toLowerCase().includes(filterString.value.toLowerCase()) || album.album.toLowerCase().includes(filterString.value.toLowerCase())
        })
        this.albumList = shortlist;
      }
  }
}

let view = ref('grid')

let filterString = ref('')

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

input {
    width: 300px;
    height: 30px;
    padding: 10px;
    border: 1px solid lightgrey;
    border-radius: 10px;
    box-shadow: 4px 4px 10px rgba(0,0,0,0.06);
    margin-bottom: 20px;
}
input:focus-visible {
    outline: none;
}
</style>
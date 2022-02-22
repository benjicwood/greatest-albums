<template>
    <!-- <img :src="require(`../assets/albumcovers/${album.cover}`)"> -->
    <!-- <div style="border:1px solid black; padding: 10px;"> -->
        <div class="flip-card">
            <div class="flip-card-inner">
                <div class="flip-card-front">
            <img :src="getAlbumCover(album.cover)" :alt="album.album" style="width: 200px; height: 200px;">
            </div>
            <div class="flip-card-back" :style="{'background-color': album.color ? album.color : 'red'}">
                <!-- <img :src="getAlbumCover(album.cover)" :alt="album.album" style="width: 200px; height: 200px; filter: brightness(0.5) blur(2px) grayscale(0.5);"> -->
                <p>{{album.position}}</p>
                <p>{{album.artist}}</p>
                <p>{{album.album}}</p>
                <p>{{album.year}}</p>
            </div>
            </div>
        </div>
</template>

<script>

//import test from "../assets/albumcovers/blink182.jpeg";

export default {
    name: 'Album',
    props: {
        album: {
            position: Number,
            artist: String,
            album: String,
            year: Number,
            cover: String,
        },
    },
    setup() {

        const getAlbumCover = (cover) => {
            if (!cover) {
                return "";
            }
            return require(`../assets/albumcovers/${cover}`); // '../assets/albumcovers/' + 
        }         

        return {
            getAlbumCover
        }
    },
}
</script>

<style scoped>
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, 200px);
    grid-gap: 10px;
}

.flip-card {
    width: 200px;
    height: 200px;
    display: grid;
    grid-template-rows: 50% 50%;
    margin-left: 10px;
    background-color: transparent;
    border: 1px solid #f1f1f1;
    perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  /* background-color: dodgerblue; */
  color: white;
  transform: rotateY(180deg);
  height: 200px;
}
/* .flip-card-back::before {
    background-image: '../assets/albumcovers/turnstileglowon.jpeg';
    filter: brightness(0.5) blur(2px) grayscale(0.5);
} */
</style>
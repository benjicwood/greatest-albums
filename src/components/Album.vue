<template>
    <!-- <img :src="require(`../assets/albumcovers/${album.cover}`)"> -->
    <!-- <div style="border:1px solid black; padding: 10px;"> -->
        <div class="flip-card">
            <div class="flip-card-inner">
                <div class="flip-card-front">
            <img :src="getAlbumCover(album.cover)" :alt="album.album" style="width: 200px; height: 200px;">
            </div>
            <div class="flip-card-back" :style="{'background-color': '#0D0A0F'}">
                <!-- <img :src="getAlbumCover(album.cover)" :alt="album.album" style="width: 200px; height: 200px; filter: brightness(0.5) blur(2px) grayscale(0.5);"> -->
                <div :style="{'color': '#0D0A0F', filter: 'brightness(3)'}" class="position">{{album.position}}</div>
                <!-- <p class="position" :style="{'color': album.color}">{{album.position}}</p> -->
                <div style="display: grid; grid-template-rows: repeat(auto-fill, 50%); height: 100%;">
                <p :style="{'color': '#0D0A0F', filter: 'invert(3)'}" class="artist">{{album.artist}}</p>
                <p :style="{'color': '#0D0A0F', filter: 'invert(3)'}" class="album">{{album.album}}</p>
                </div>
                                <p :style="{'color': '#0D0A0F', filter: 'invert(3)'}" class="year">{{album.year}}</p>
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
    font-size: 9.5rem;
    font-weight: 600;
    font-family: system-ui;
    font-weight: 700;
}
.flip-card-back p {
    margin: 0 5px;
    font-weight: bold;
}
.position {
    /* font-size: 14rem;
    font-weight: bold;
    position: absolute;
    width: 200px;
    height: 240px;
    margin: 0;
    bottom: 5px;
    filter: brightness(5);
    z-index: -1; */
    position: absolute;
    width: 100%;
    height: 100%;
}
.year {
    position: fixed;
    margin: auto;
    bottom: 0;
    width: 100%;
    font-size: 1.1rem;
}
.artist {
    margin-top:50px;
    font-size: 1.8rem;
    line-height: 1.8rem;
    color: white;
    align-self: flex-end;
    padding-bottom: 10px;
    border-bottom: 1px solid rgb(13, 10, 15);
}
.album {
    color: white;
    font-weight: bold;
    line-height: 1.2rem;
    margin-top: 8px;
    font-size: 1.1rem;
    padding-top: 5px;
}
/* .flip-card-back::before {
    background-image: '../assets/albumcovers/turnstileglowon.jpeg';
    filter: brightness(0.5) blur(2px) grayscale(0.5);
} */
</style>
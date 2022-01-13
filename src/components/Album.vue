<template>
    <!-- <img :src="require(`../assets/albumcovers/${album.cover}`)"> -->
    <div style="border:1px solid black; padding: 10px;">
        <img :src="getAlbumCover(album.cover)" :alt="album.album" style="width: 200px; height: 200px;">
        <div>{{album.position}}</div>
        <div>{{album.artist}}</div>
        <div>{{album.album}}</div>
        <div>{{album.year}}</div>
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

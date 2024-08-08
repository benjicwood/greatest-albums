<template>
<div class="album-box">
    <img :src="getAlbumCover(album.cover)" :alt="`${album.artist} - ${album.album} album cover`">
    <p class="album-number">{{ album.position }}</p>
    <p class="album-name">{{ album.artist }} - {{ album.album }}</p>
    <p class="album-year">{{ album.year }}</p> 
</div>
</template>

<script>
export default {
    name: 'ListItem',
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
            return require(`../assets/albumcovers/${cover}`);
        }         

        return {
            getAlbumCover
        }
    },
}
</script>

<style scoped>
.album-box {
    display: flex;
    border: 1px solid #cacaca;
    border-radius: 3px;
    width: 80%;
    margin: 0.5rem auto;
    background: #f7f7f7;
}
.album-box img {
    height: 60px;
    padding: 0.25rem;
}
.album-box p {
    padding: 0.25rem;
    margin: auto 0;
}
.album-number {
    font-weight: bold;
    font-size: 30px;
}
.album-name {
    width: 100%;
    text-align: left;
}
.album-year {
    font-weight: 500;
}
</style>

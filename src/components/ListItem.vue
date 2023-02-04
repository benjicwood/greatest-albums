<template>
    <p>{{ album.position }}: {{ album.artist }} - {{ album.album }}</p>
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

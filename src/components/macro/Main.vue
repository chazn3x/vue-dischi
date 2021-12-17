<template>
    <main>
        <AlbumsList :albums="albums" :loader="response" :info="{genres: genres, artists: artists}"/>
    </main>
</template>

<script>
import axios from 'axios';
import AlbumsList from '../sections/AlbumsList.vue'
export default {
    name: "Main",
    components: {
        AlbumsList
    },
    data() {
        return {
            albums: [],
            genres: [],
            artists:[],
            response: false,
        }
    },
    created() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.albums = response.data.response;
            this.albums.forEach(album => {
                if (!(this.genres.includes(album.genre))) {
                    this.genres.push(album.genre);
                }
                if (!(this.artists.includes(album.author))) {
                    this.artists.push(album.author);
                }
            });
            this.response = true;
        });
    }
}
</script>

<style lang="scss" scoped>

</style>
<template>
    <main>
        <AlbumsList v-if="albums.length == 10" :albums="albums"/>
        <div v-else class="loader"></div>
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
        }
    },
    mounted() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            this.albums = response.data.response;
        });
    }
}
</script>

<style lang="scss" scoped>
.loader {
    width: 60px;
    height: 60px;
    margin: 150px auto;
    border-radius: 50%;
    border: 4px solid rgb(45,58,70);
    border-top: 4px solid rgb(28,215,96);
    // border: 4px solid rgb(28,215,96);
    animation: spin 1s linear infinite;
    @keyframes spin {
        0% {transform: rotate(0deg);}
        100% {transform: rotate(360deg);}
    }
}
</style>
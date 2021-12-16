<template>
    <main>
        <AlbumsList :albums="albums"/>
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
            albums: null,
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

</style>
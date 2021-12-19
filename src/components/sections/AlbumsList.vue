<template>
    <section class="container">
        <Search :info="info" @search="searchAlbums"/>
        <div v-if="loader" class="list">
            <AlbumCard v-for="(album, index) in filteredAlbums" :key="index" :info="album" :search="filter"/>
        </div>
        <div v-else class="loader"></div>
    </section>
</template>

<script>
import AlbumCard from '../commons/AlbumCard.vue'
import Search from '../commons/Search.vue'
export default {
    name: "AlbumsList",
    props: {
        albums: Array,
        loader: Boolean,
        info: Object
    },
    components: {
        AlbumCard,
        Search
    },
    data() {
        return {
            filter: '',
        }
    },
    methods: {
        searchAlbums(payload) {
            this.filter = payload;
        }
    },
    computed: {
        filteredAlbums() {
            return this.albums.filter(album => {
                if (album.genre == this.filter) {
                    return album;
                }
                if (album.author == this.filter) {
                    return album;
                }
                if (album.author.toLowerCase().includes(this.filter.toLowerCase()) || album.title.toLowerCase().includes(this.filter.toLowerCase())) {
                    return album;
                }
                if (this.filter == '') {
                    return album;
                }
            });
        },
    }
}
</script>

<style lang="scss" scoped>
section {
    .list {
        padding: 50px 0;
        display: grid;
        justify-content: center;
        grid-template-columns: repeat(auto-fill, 190px);
        column-gap: 30px;
        row-gap: 20px;
    }
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
}
</style>
<template>
    <div class="search">
        <!-- ricerca album o artista -->
        <div class="search-bar">
            <div class="icon search-icon">
                <svg role="img" height="24" width="24" class="Svg-sc-1bi12j5-0 hDgDGI mOLTJ2mxkzHJj6Y9_na_" aria-hidden="true" viewBox="0 0 24 24"><path d="M16.387 16.623A8.47 8.47 0 0019 10.5a8.5 8.5 0 10-8.5 8.5 8.454 8.454 0 005.125-1.73l4.401 5.153.76-.649-4.399-5.151zM10.5 18C6.364 18 3 14.636 3 10.5S6.364 3 10.5 3 18 6.364 18 10.5 14.636 18 10.5 18z"></path></svg>
            </div>
            <input type="text" placeholder="Search for albums or artists" v-model="searchText" @keyup="del = !(searchText == ''), $emit('search', searchText), genre = '', artist = ''">
            <div :class="{'active': del}" class="icon delete-icon" @click="searchText = '', $emit('search', searchText), del = false">
                <svg role="img" height="24" width="24" class="Svg-sc-1bi12j5-0 hDgDGI mOLTJ2mxkzHJj6Y9_na_" viewBox="0 0 24 24"><path d="M20.354 4.353l-.708-.706L12 11.293 4.353 3.647l-.706.706L11.293 12l-7.646 7.646.706.708L12 12.707l7.646 7.647.708-.708L12.707 12z"></path></svg>
            </div>
        </div>
        <!-- ricerca per genere -->
        <div class="genres">
            <span>Select a genre: </span>
            <select v-model="genre" @change="$emit('search', genre), artist = '', searchText = '', del = false">
                <option value="" selected>All</option>
                <option v-for="(genre, index) in info.genres" :key="index" :value="genre">{{genre}}</option>
            </select>
        </div>
        <!-- ricerca per artista -->
        <div class="artists">
            <span>Select an artist: </span>
            <select v-model="artist" @change="$emit('search', artist), genre = '', searchText = '', del = false">
                <option value="" selected>All</option>
                <option v-for="(artist, index) in info.artists" :key="index" :value="artist">{{artist}}</option>
            </select>
        </div>
    </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'
export default {
    name: "Search",
    props: {
        info: Object
    },
    data() {
        return {
            genre: '',
            artist: '',
            searchText: '',
            del: false
        }
    }
}
</script>

<style lang="scss" scoped>
.search {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
    span {
        color: white;
        margin-right: 10px;
    }
    .search-bar, .genres, .artists {
        margin: 0 20px;
    }
    .search-bar {
        width: 300px;
        height: 40px;
        background-color: #fff;
        border-radius: 20px;
        display: flex;
        align-items: center;
        justify-content: space-around;
        input {
            height: 100%;
            border: none;
            outline: none;
            background: transparent;
            width: 70%;
            font-size: 1rem;
            &::placeholder {
                font-size: .85rem;
            }
        }
        .icon {
            display: flex;
            align-items: center;
            svg {
                width: 20px;
            }
            &.delete-icon {
                opacity: 0;
                &.active {
                    opacity: 1;
                }
            }
        }
        
    }
}
</style>
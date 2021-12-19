<template>
    <div class="album-card">
        <div class="img">
            <img :src="info.poster" :alt="info.title + ' cover'">
        </div>
        <h3 v-if="search.length == 1">
            <span v-for="(part, index) in info.title" :key="index"><span :class="{'match': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </h3>
        <h3 v-else>
            <span v-for="(part, index) in filteredTitle" :key="index"><span :class="{'match': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </h3>
        <p v-if="search.length == 1">
            <span v-for="(part, index) in info.author" :key="index"><span :class="{'match': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </p>
        <p v-else>
            <span v-for="(part, index) in filteredAuthor" :key="index"><span :class="{'match': part.toLowerCase() == search.toLowerCase()}">{{part}}</span></span>
        </p>
        <p>{{info.year}}</p>
    </div>
</template>

<script>
export default {
    name: "AlbumCard",
    props: {
        info: Object,
        search: String
    },
    computed: {
        filteredTitle() {
            let name = this.info.title.toLowerCase().split(`${this.search.toLowerCase()}`);
            if (this.info.title.toLowerCase().includes(this.search.toLowerCase())) {
                name.splice(1, 0, this.search.toLowerCase());
            }
            return name;
        },
        filteredAuthor() {
            let name = this.info.author.toLowerCase().split(`${this.search.toLowerCase()}`);
            if (this.info.author.toLowerCase().includes(this.search.toLowerCase())) {
                name.splice(1, 0, this.search.toLowerCase());
            }
            return name;
        },
    }
}
</script>

<style lang="scss" scoped>
.album-card {
    background: rgb(45,58,70);
    padding: 15px;
    text-align: center;
    border-radius: 3px;
    color: white;
    .img {
        width: 100%;
        aspect-ratio: 1;
        overflow: hidden;
        margin-bottom: 10px;
        img {
            width: 100%;
        }
    }
    h3 {
        margin-bottom: 15px;
        text-transform: uppercase;
    }
    p {
        text-transform: capitalize;
        opacity: .4;
    }
    .match {
        color: rgb(0,216,87);
    }
}
</style>
<template>
    <div class="album-card">
        <div class="img">
            <img :src="info.poster" :alt="info.title + ' cover'">
        </div>
        <h2>{{info.title}}</h2>
        <p>{{info.author}}</p>
        <p>{{info.year}}</p>
    </div>
</template>

<script>
export default {
    name: "AlbumCard",
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
.album-card {
    background: rgb(45,58,70);
    padding: 15px;
    text-align: center;
    color: white;
    .img {
        width: 100%;
        aspect-ratio: 1;
        margin-bottom: 10px;
        img {
            width: 100%;
        }
    }
    h2 {
        margin-bottom: 15px;
    }
}
</style>
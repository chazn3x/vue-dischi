<template>
    <div class="album-card">
        <div class="img">
            <img :src="info.poster" :alt="info.title + ' cover'">
        </div>
        <h3>{{info.title}}</h3>
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
    border-radius: 3px;
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
        color: white;
        text-transform: uppercase;
    }
    p {
        color: rgba(255,255,255,0.4);
    }
}
</style>
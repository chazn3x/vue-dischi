<template>
    <section class="container">
        <AlbumCard v-for="(album, index) in albums" :key="index" :info="album"/>
    </section>
</template>

<script>
import AlbumCard from '../commons/AlbumCard.vue'
export default {
    name: "AlbumsList",
    props: {
        albums: Array
    },
    components: {
        AlbumCard,
    }
}
</script>

<style lang="scss" scoped>
section {
    padding: 50px 0;
    display: grid;
    justify-content: center;
    grid-template-columns: repeat(auto-fill, 190px);
    column-gap: 30px;
    row-gap: 20px;
}
</style>
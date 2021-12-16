<template>
    <main>

    </main>
</template>

<script>
import axios from 'axios';
export default {
    name: "Main",
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
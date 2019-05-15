<template>
    <li class="list-group-item">
        <img :src="thumbnailURL">
        {{ videoElement.snippet.title }}
    </li>
</template>

<script>
export default {
    name: "VideoListItem",
    props: {
        videoElement: Object
    },
    computed: {
        thumbnailURL() {
            return this.videoElement.snippet.thumbnails.default.url;
        }
    }
}
</script>

<style>

</style>

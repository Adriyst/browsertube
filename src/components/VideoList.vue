<template>
    <ul class="list-group">
        <VideoListItem 
            v-for="video in childVideos"
            :videoElement="video"
            :key="video.etag"
        >
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';
export default {
    name: "VideoList",
    props: {
        childVideos: Array
    },
    components: {
        VideoListItem
    }
}
</script>

<style>

</style>

<template>
    <ul class="list-group col-md-4">
        <VideoListItem 
            v-for="video in childVideos"
            :videoElement="video"
            :key="video.etag"
            @onSelectedVideo="passVideo" 
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
    },
    methods: {
        passVideo(v) {
            this.$emit('onSelectedVideo', v);
        }
    }
}
</script>

<style scoped>

</style>

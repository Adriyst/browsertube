<template>
    <li class="list-group-item media" @click="onSelection">
        <img :src="thumbnailURL" class="mr-3">
        <div class="media-body">
            {{ videoElement.snippet.title }}
        </div>
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
    },
    methods: {
        onSelection() {
            this.$emit('onSelectedVideo', this.videoElement);
        }
    }
}
</script>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }
    
    li:hover {
        background: #eee;
    }
</style>

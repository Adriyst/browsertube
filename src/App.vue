<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div id="row">
            <VideoDetail :video="currentVideo"></VideoDetail>
            <VideoList 
                :childVideos="videos"
                @onSelectedVideo="updateCurrentVideo"
            ></VideoList>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = '';


export default {
    name: 'App',
    components: {
        SearchBar, 
        VideoList, 
        VideoDetail
    },
    data(){
        return {
            videos: [],
            currentVideo: null
        }
    },
    methods: {
        onTermChange(e) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: e
                }
            }).then(r => {
                this.videos = r.data.items;
            });
        },
        updateCurrentVideo(v) {
            this.currentVideo = v;
        }
    }
};
</script>

<style scoped>
    #row {
        display: flex;
        flex-direction: row;
    }
</style>

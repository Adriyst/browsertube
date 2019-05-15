<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :childVideos="videos"></VideoList>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

const API_KEY = 'AIzaSyDC3Pg0mjEyVTHuYHpWoAaGhC9QKqwlVVE';


export default {
    name: 'App',
    components: {
        SearchBar, VideoList
    },
    data(){
        return {
            videos: []
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
        }
    }
};
</script>
<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';

const API_KEY = '';


export default {
    name: 'App',
    components: {
        SearchBar
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
            }).then(r => console.log(r));
            
        }
    }
};
</script>
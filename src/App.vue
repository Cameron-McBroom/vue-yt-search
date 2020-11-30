<template>
    <div class="container">
        <SearchBar @newSearch="onNewSearch" :video="selectedVideo"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo"> </VideoDetail>
            <VideoList :videos="videos" @videoClicked="onVideoClick"> </VideoList>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetail from './components/VideoDetail.vue';

const API_KEY = 'AIzaSyA7NNm5qL6kTxWcH30I50ELc_jQDx-BSAM';

export default {
    components: { SearchBar, VideoList, VideoDetail },
    name: 'App',
    data () {
        return { videos: [], selectedVideo: null };
    },
    methods: {
        onNewSearch(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet', // only returns small amount of data
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            })
        },
        onVideoClick(video) {
            this.selectedVideo = video;
        } 
    }
};
</script>
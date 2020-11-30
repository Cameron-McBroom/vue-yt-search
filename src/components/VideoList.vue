<template>
    <ul class="col-md-4">
        <VideoListItem 
            v-for="video in videos" 
            :key="video.etag" 
            :video="video"
            @videoClicked="onVideoClick"    
        >

        </VideoListItem>
    </ul>
</template>

<script>

import VideoListItem from './VideoListItem.vue';

export default {
    name: 'VideoList',
    components: { VideoListItem },
    props: { videos: Array, video: Object },
    methods: {
        onVideoClick(video) {
            this.$emit('videoClicked', video);
        }
    }
}
</script>

<style>

</style>
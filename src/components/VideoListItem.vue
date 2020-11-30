<template>

<li class="list-group-item media" @click="onVideoClick"> 
    <img :src="thumbnailUrl" class="mr-3"/>
    <div class="media-body">
        {{ video.snippet.title }}
    </div>
</li>

</template>

<script>
export default {
    name:'VideoListItem',
    props: { video: Object },
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoClick() {
            this.$emit('videoClicked', this.video);
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
        background-color: #eee;
    }
</style>
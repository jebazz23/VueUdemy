<template>
    <ul class="list-group col-md-4">
       <VideoListItem v-for="video in myListOfVideos" :key="video.etag" :videoDetail="video" @videoSelect="onVideoSelect"></VideoListItem>
    </ul>
</template>
<script>
import VideoListItem from './VideoListItem.vue';
export default {
    name: 'VideoList',
    components:{
        VideoListItem
    },
    props:['myListOfVideos'],
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect', video);
        }
    }
}
</script>
<style lang="">
    
</style> 
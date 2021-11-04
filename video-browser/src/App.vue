<template>
    <div class="container"> 
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
        <VideoDetail :video="selectedVideo" /> 
        <VideoList @videoSelect="onVideoSelect" :myListOfVideos="videos"></VideoList>
        </div>
  
    </div>
</template>
<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoList from  './components/VideoList.vue';
import VideoDetail from './components/VideoDetail.vue';

const API_KEY = 'AIzaSyBissx3lxH_uGZe8KPK6NrwABqBeRhV7JY';

export default {
    name:'App',
    components:{
        SearchBar,
        VideoList,
        VideoDetail 
    },
    data(){
        return {
            videos:[],
            selectedVideo: null
        };
    },
    methods:{
        onVideoSelect(video){
            this.selectedVideo = video;
            console.log(video);
        },
        onTermChange(searchTerm) {
            console.log(searchTerm);
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params:{
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
                console.log(this.videos)
            })
        }
    }
}
</script>
<style>
    
</style>
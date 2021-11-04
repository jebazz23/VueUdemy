<template>
    <li class="list-group-item" @click="onVideoSelect">
        <img class="m-3" :src="thumbnailUrl" alt="">
        <div class="media-body">
        {{videoDetail.snippet.title}}
        </div>

    </li>
</template>
<script>
export default {
    name:'VideoListItem',
    props:['videoDetail'],
    computed:{
        thumbnailUrl(){
            return this.videoDetail.snippet.thumbnails.default.url;
        },
    },
    methods:{
        onVideoSelect(){
            this.$emit('videoSelect', this.videoDetail);
        }
    }
}
</script>
<style scoped>
   li {
       display: flex;
       cursor: pointer;
   } 

   li:hover{
       background-color: #eee;
   }

</style>
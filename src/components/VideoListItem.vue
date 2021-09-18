<template>
    <div>
        <li class="list-group-item media" @click="onVideoSelect">
            <img class="mr-4" :src="addThumbnail">
            <div class="media-body">
                 Video List item {{video.snippet.title}}
             <h6 class="my-1">Channel: {{video.snippet.channelTitle}}</h6>
             <p>Release date: {{video.snippet.publishTime}}</p>
            </div>            
        </li>
    </div>
</template>

<script>

export default {
    props: ['video'],
    name: "VideoListItem",
    // data(){
    //     return {
    //         thumbnail : [],
    //     }
    // },

    computed: {
        addThumbnail(){
           return this.video.snippet.thumbnails.default.url
           
        } 
    },
    methods: {
       onVideoSelect(){
            this.$emit('videoSelect', this.video)
        }
    }

}
</script>

<style scoped>
li{
    display: flex;
    cursor: pointer;

}
img{
    margin-right: 25px;
}
li:hover{
    background-color: #eee;
}
</style>
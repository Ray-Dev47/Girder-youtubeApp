<template>
  <div class="container">
    <search-bar @termChange="onTermChange"></search-bar>
    <div class="row">
      <video-detail :video="selectedVideo"></video-detail>
      <video-list :videos="videos" @videoSelect="onVideoSelect"></video-list>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/videoDetail.vue";
const API_KEY = "AIzaSyAAkLyb9OgBrCKGYMv9b9R0gvRF-EyNIxg";

export default {
  components: { SearchBar, VideoList, VideoDetail },
  name: "App",
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          //attach api key
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet", // tells the type of info we want to get back
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
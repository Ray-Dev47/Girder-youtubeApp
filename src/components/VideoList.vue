<template>
  <div class="list-group col-md-4">
    <video-list-item
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
    >
    </video-list-item>
  </div>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";
export default {
  components: { VideoListItem },
  name: "VideoList",
  props: {
    videos: {
      type: Array,
      required: true,
    },
  },
  // emit data
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style scoped>
</style>
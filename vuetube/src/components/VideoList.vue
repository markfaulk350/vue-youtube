<template>
  <ul class="list-group col-md-4">
    <VideoListItem @videoSelect="onVideoSelect" v-for="video in videos" :video="video" :key="video.id.videoId">
      <!--
       <VideoListItem 
       v-for="video in videos"   // Loops through each video in data and assigns value to 'video'
       :video="video"     // : passes the video value we just assigned, down as props to child component
       :key="video.id.videoId"
       >
      -->
    </VideoListItem>
  </ul>
</template>



<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  },
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video )
    }
  }
};
</script>

<style scoped>
</style>
<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row">
    <VideoDetail :video="selectedVideo"/>
    <VideoList @videoSelect="onVideoSelect" v-bind:videos="videos" />
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'
import axios from 'axios'
const API_KEY = ''

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
      return {
          videos: [],
          selectedVideo: null
      }
  },
  methods: {
      onTermChange(searchTerm) {
          axios.get('https://www.googleapis.com/youtube/v3/search', {
              params: {
                  key: API_KEY,
                  type: 'video',
                  part: 'snippet',
                  q: searchTerm
              }
          }).then(response => {
              console.log(response)
              this.videos = response.data.items
          })
      },
      onVideoSelect(video) {
        // console.log(video);
        this.selectedVideo = video;
      }
  },
};
</script>

<style scoped>
</style>
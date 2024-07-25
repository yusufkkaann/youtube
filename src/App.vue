<template>
  <div class="container">
    <h1 class="title">Youtube uygulaması</h1>
    <SearchBar @searchValue="inputValue" />
    <div class="videoContainer">
      <VideoDetails v-if="selectedVideo" :selectedVideo="selectedVideo" />

      <Videos @videoSelected="onVideoSelected" :videos="videos" />
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import axios from "axios";
import Videos from "./components/Videos.vue";
import VideoDetails from "./components/VideoDetails.vue";

export default {
  name: "App",
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  components: {
    SearchBar,
    Videos,
    VideoDetails,
  },
  methods: {
    onVideoSelected(video) {
      this.selectedVideo = video;
    },
    inputValue(value) {
      this.selectedVideo = null;
      // console.log(value);
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            part: "snippet",
            type: "video",
            // maxResults: 5,
            key: "AIzaSyDmg5PRQutra6j28Gx3-4CoaoYng5VOqnM",
            q: value,
          },
        })
        .then((response) => {
          console.log(response);
          this.videos = response.data.items;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  max-width: 1200px;
  width: 100%;
  margin: 50px auto;
}
.title {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 20px;
}
.videoContainer {
  display: flex;
  justify-content: space-between;

  gap: 60px;
}
</style>

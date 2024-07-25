<template>
  <ul class="videoList">
    <VideoList
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoSelected="onVideoSelected"
    />
  </ul>
</template>

<script>
import VideoList from "./VideoList.vue";

export default {
  name: "VideosContainer",
  props: ["videos"],
  components: {
    VideoList,
  },

  data() {
    return {};
  },
  methods: {
    onVideoSelected(video) {
      this.$emit("videoSelected", video);
    },
  },
  emits: ["videoSelected"],
};
</script>

<style scoped>
.videoList {
  list-style: none;
  margin-top: 40px;
  width: 100%;
}
</style>

<template>
  <div v-if="selectedVideo" class="videoDetails">
    <iframe class="video" :src="videoUrl" frameborder="0"></iframe>
    <div class="videoDescription">
      <h2>{{ selectedVideo.snippet.title }}</h2>
      <p>{{ selectedVideo.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["selectedVideo"],
  name: "VideoDetails",
  computed: {
    videoUrl() {
      const videoId = this.selectedVideo.id.videoId;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.videoDetails {
  margin-top: 40px;
  margin-top: 70px;
  width: 100%;
}
.video {
  width: 100%;
  height: 350px;
}
.videoDescription {
  border: 1px solid red;
  border-radius: 20px;
  padding: 20px;
}
.videoDescription h2 {
  font-size: 2rem;
}
.videoDescription p {
  font-size: 1.5rem;
}
</style>

<template>
  <li class="videoItem" @click="onVideoSelected">
    <img class="videoImg" :src="imageUrl" />
    <div class="videoDescription">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  props: ["video"],
  computed: {
    imageUrl() {
      return this.video.snippet.thumbnails.medium.url;
    },
  },
  methods: {
    onVideoSelected() {
      this.$emit("videoSelected", this.video);
    },
  },
  emits: ["videoSelected"],
};
</script>

<style scoped>
.videoItem {
  display: flex;
  align-items: center;
  border: 1px solid red;
  border-radius: 20px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  margin: 30px 0px;
  cursor: pointer;
}
.videoImg {
  border-radius: 20px 0px 0px 20px;
  margin-right: 40px;
}
.videoDescription {
  font-size: 1.5rem;
}
</style>

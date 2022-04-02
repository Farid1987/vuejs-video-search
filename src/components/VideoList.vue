<template>
  <ul class="list-group col-md">
    <VideoListItem
      v-for="video in videos"
      :video="video"
      :key="video.etag"
      @videoSelect="onVideoSelect"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";

export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: {
    videos: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style lang="">
</style>
<template>
  <div v-if="video" class="col-md-8">
    <div class="ratio ratio-16x9">
      <iframe :src="videoUrl" frameborder="0" allow="autoplay"></iframe>
    </div>
    <div class="details">
      <h4 class="">{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: {
    video: {
      type: [Object, null],
    },
  },
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.video.id.videoId}?autoplay=1`;
    },
  },
};
</script>

<style lang="scss" scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
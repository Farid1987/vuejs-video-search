<template>
  <li class="list-group-item media d-flex" @click="onVideoSelect">
    <img class="me-3" :src="thumbnailUrl" alt="video-thumbnail" />
    <div class="media-body">
      {{ decodeText(video.snippet.title) }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: {
      type: Object,
    },
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    decodeText(text) {
      var txt = document.createElement("textarea");
      txt.innerHTML = text;
      return txt.value;
    },
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style lang="scss" scoped>
li {
  cursor: pointer;
  transition: all 0.2s;
  &:hover {
    background-color: #eee;
  }
}
</style>
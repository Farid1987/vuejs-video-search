<template>
  <div>
    <SearchBar @termChange="onSearch" />
    <div class="container">
      <div class="row">
        <VideoDetail :video="selectedVideo" />
        <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

const API_KEY = "AIzaSyBPgLC1sI2O58fwAZa0NPSWmokutDk2foc";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onSearch(value) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: value,
          },
        })
        .then((res) => {
          if (res.status === 200 && res.data) {
            this.videos = res.data.items;
          }
        });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
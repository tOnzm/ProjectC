<template>
  <div>
    <carouselsImage />
    <moviesThumbnail :titleText="'ภาพยนตร์มาใหม่'">
      <div v-for="item in movies" :key="item.id">
        <thumbnail
          :thumbnailImage="item.poster_path"
          :path="item.id"
          :backdropImage="item.backdrop_path"
          :moviesLogo="item.file_path"
          :languagesData="item.spoken_languages"
          :time="item.runtime"
          :contentRating="item.certification"
          :front="'movies'"
        >
        </thumbnail>
      </div>
    </moviesThumbnail>
    <bottomNav />
  </div>
</template>

<script>
import carouselsImage from "@/components/carouselsImage/index.vue";
import studioMenu from "@/components/studioMenu/index.vue";
import moviesThumbnail from "@/components/moviesThumbnail/index";
import thumbnail from "@/components/moviesThumbnail/thumbnail/index.vue";
import { Movies } from "@/api/api.js";
export default {
  name: "IndexPage",
  components: { carouselsImage, moviesThumbnail, thumbnail, studioMenu },
  head: {
    title: " หน้าแรก",
  },
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    async Movies() {
      const data = this.$axios;
      this.movies = await Movies(data);
    },
  },
  mounted() {
    this.Movies();
  },
};
</script>

<style lang="scss" scoped></style>

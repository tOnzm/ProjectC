<template>
  <div>
    <h1>{{ movie.original_title }}</h1>
    <img :src="getImageUrl(movie.poster_path)" :alt="movie.original_title" />
    <p>{{ movie.overview }}</p>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    try {
      const response = await $axios.$get(
        `https://api.themoviedb.org/3/movie/${params.id}?api_key=3c79a5d5b0c2bd68652652a202b1c175`
      );
      return { movie: response || {} };
    } catch (error) {
      console.error(`Error fetching movie data for ${params.id}`, error);
      return { movie: {} };
    }
  },
  methods: {
    getImageUrl(posterPath) {
      const baseImageUrl = "https://image.tmdb.org/t/p/w500/";
      return `${baseImageUrl}${posterPath}`;
    },
  },
};
</script>

<style lang="scss" scoped>
.photo-info {
  width: 860px;
  margin: 0 auto;
  text-align: center;
}
.img {
  width: 200px;
}

.link {
  display: inline-block;
  margin-top: 2em;
}
</style>

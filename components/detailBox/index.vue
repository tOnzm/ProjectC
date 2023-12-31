<template>
  <div class="detail-box" flat>
    <div class="logoBox">
      <img class="movie-logo" :src="getLogoUrl(moviesLogo)" :alt="{ alt }" />
    </div>
    <div>
      <div class="movie-detail">
        <v-icon class="detail-icons">mdi-calendar</v-icon>
        <h3>{{ movieYear(year) }}</h3>
        <v-icon class="icon-dot">mdi-circle-small</v-icon>
        <v-icon class="detail-icons">mdi-volume-high</v-icon>
        <h3>{{ languages(voice) }}</h3>
        <v-icon class="icon-dot">mdi-circle-small</v-icon>
        <v-icon class="detail-icons">mdi-timer</v-icon>
        <h3>{{ movieTime(time) }}</h3>
        <v-icon class="icon-dot">mdi-circle-small</v-icon>
        <div class="movie-rating">
          <h3>{{ certification(contentRating) }}</h3>
        </div>
      </div>
      <div class="movie-overview">
        <h4>{{ overview(overviewData) }}</h4>
      </div>
      <div class="movie-genres">
        <h4>{{ genres(genresData) }}</h4>
      </div>
    </div>
    <div>
      <v-row dense>
        <v-col cols="8" md="10">
          <NuxtLink :to="`${front}/${path}`">
            <playNowBtn
              :prepend-icon="'mdi-play'"
              :text="'รับชมเดี๋ยวนี้'"
              :color="'#ffffff'"
              :icon-color="'#000'"
              :text-color="'#000'"
              :btnSize="'x-large'"
              :btn-block="true"
              :btnLarge="true"
            />
          </NuxtLink>
        </v-col>
        <v-col cols="1" md="2"
          ><playNowBtn :prepend-icon="'mdi-plus'" :btnLarge="true"
        /></v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
import playNowBtn from "../buttons/playNowBtn/index";
import {
  getImageUrl,
  movieYear,
  movieTime,
  getLogoUrl,
  genres,
  languages,
  overview,
  certification,
} from "@/api/api";

export default {
  name: "DetailBox",
  components: { playNowBtn },
  props: {
    year: String,
    voice: null,
    contentRating: null,
    overviewData: String,
    genresData: null,
    moviesLogo: String,
    path: null,
    time: Number,
    alt: String,
    front: String,
  },
  methods: {
    getImageUrl(imagePath) {
      return getImageUrl(imagePath);
    },
    getLogoUrl(logoPath) {
      return getLogoUrl(logoPath);
    },

    movieYear(year) {
      return movieYear(year);
    },
    movieTime(time) {
      return movieTime(time);
    },
    genres(genresData) {
      return genres(genresData);
    },
    languages(languagesData) {
      return languages(languagesData);
    },
    overview(overviewData) {
      return overview(overviewData);
    },
    certification(certificationData) {
      return certification(certificationData);
    },
  },
};
</script>

<style lang="scss" scoped>
.detail-box {
  width: 500px;
  height: 100%;
  margin: 1rem;
  position: absolute;
  top: 5%;
  left: 10%;
  background: transparent;
  z-index: 999;
}
//โลโก้
.logoBox {
  width: 100%;
  .movie-logo {
    width: fit-content;
    object-fit: contain;
    aspect-ratio: 16/9;
  }
}
//ข้อมูลทั่วไป
.movie-detail {
  display: flex;
  align-items: center;
  h3 {
    font-size: 1.2rem;
  }
  .detail-icons {
    color: #d8d8d8;
    font-size: 1rem;
    padding-right: 0.5rem;
  }
  .icon-dot {
    color: #d8d8d8;
    font-size: 1rem;
  }
}
//เรทอายุ
.movie-rating {
  display: flex;
  background-color: #fff2;
  backdrop-filter: blur(5px);
  max-width: 100px;
  padding: 2px 8px;
  border-radius: 5px;
  h3 {
    font-weight: 600;
    font-size: 1.2rem;
    text-align: center;
  }
}

//เรื่องย่อ
.movie-overview {
  margin: 0.5rem 0;
  h4 {
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    color: #ffffff90;
    font-weight: 400;
  }
}
//ประเภท
.movie-genres {
  margin: 0.75rem 0;
  h4 {
    font-size: 1rem;
    font-weight: 500;
  }
}

@media screen and(max-width: 600px) {
  .detail-box {
    width: 100%;
    height: 50px;
    margin: 0rem;
    padding: 0rem;
    position: absolute;
    top: 0%;
    left: 0%;
    background: transparent;
    z-index: 999;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  //โลโก้ res 600px
  .logoBox {
    width: 100%;
    display: flex;
    justify-content: center;
    .movie-logo {
      width: fit-content;
      object-fit: contain;
      aspect-ratio: 16/9;
    }
  } 
  //ข้อมูลทั่วไป
  .movie-detail {
    display: flex;
    align-items: center;
    h3 {
      font-size: 0.75rem;
    }
    .detail-icons {
      color: #d8d8d8;
      font-size: 1rem;
      padding-right: 0.5rem;
    }
    .icon-dot {
      color: #d8d8d8;
      font-size: 1rem;
    }
  }
  .movie-overview {
    display: none;
  }
  .movie-genres {
    display: none;
  }
}

@media screen and(max-width: 960px) {
  .detail-box {
    width: 100%;
    height: 250px;
    margin: 0rem;
    padding: 0rem;
    position: absolute;
    top: 10%;
    left: 0%;
    background: transparent;
    z-index: 999;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
//โลโก้ res 960px
.logoBox {
    width: 100%;
    display: flex;
    justify-content: center;
    .movie-logo {
      width: fit-content;
      object-fit: contain;
      aspect-ratio: 16/9;
    }
  } 
  //ข้อมูลทั่วไป
  .movie-detail {
    display: flex;
    align-items: center;
    h3 {
      font-size: 1rem;
    }
    .detail-icons {
      color: #d8d8d8;
      font-size: 1rem;
      padding-right: 0.5rem;
    }
    .icon-dot {
      color: #d8d8d8;
      font-size: 1rem;
    }
  }
  .movie-overview {
    display: none;
  }
  .movie-genres {
    display: none;
  }
}

@media screen and(max-width: 1264px) {
  .detail-box {
    width: 100%;
    height: 300px;
    margin: 0rem;
    padding: 0rem;
    position: absolute;
    top: 10%;
    left: 0%;
    background: transparent;
    z-index: 999;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  .movie-logo {
    max-width: 80%;
    height: 150px;
    object-fit: scale-down;
  }
  .movie-detail {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 40px;
    font-size: 0.8rem;
  }
  .movie-overview {
    width: 500px;
    height: 100px;
    text-align: center;
  }
  .movie-genres {
    display: none;
  }
}
</style>

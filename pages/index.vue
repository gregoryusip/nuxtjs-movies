<template>
  <!-- <Tutorial/> -->
  <div class="container px-4">
    <h1 class="font-bold text-4xl text-rose-700 text-center mb-10 bg-sky-400">
      List of Film
    </h1>

    <div class="mb-10">
      <div class="w-full px-4">
        <h3 class="font-semibold text-3xl text-slate-700 mb-5 px-4">
          Now Playing 👀
        </h3>
      </div>

      <div class="border-t-4 border-red-800 mb-5"></div>

      <div class="w-full px-4 flex flex-wrap mx-auto justify-center">
        <div
          v-for="movie in movies"
          :key="movie.id"
          class="mb-10 px-4 md:w-1/3 lg:w-1/4 xl:w-1/5"
        >
          <div class="rounded-lg shadow-md overflow-hidden">
            <nuxt-link
              :to="{ name: 'movies-movieid', params: { movieid: movie.id } }"
            >
              <img
                :src="`https://image.tmdb.org/t/p/w400${movie.poster_path}`"
                alt=""
                width="w-full"
              />
            </nuxt-link>
          </div>
          <div class="">
            <nuxt-link
              :to="{ name: 'movies-movieid', params: { movieid: movie.id } }"
            >
              <h2 class="font-bold text-slate-700 text-lg text-center my-5">
                {{ movie.title }}
              </h2>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>

    <div class="mb-10">
      <div class="w-full px-4">
        <h3 class="font-semibold text-3xl text-slate-700 mb-5 px-4">
          Popular Movies 🔥
        </h3>
      </div>

      <div class="border-t-4 border-red-800 mb-5"></div>

      <div class="w-full px-4 flex flex-wrap mx-auto justify-center">
        <div
          v-for="popular in popularMovies"
          :key="popular.id"
          class="mb-10 px-4 md:w-1/3 lg:w-1/4 xl:w-1/5"
        >
          <div class="rounded-lg shadow-md overflow-hidden">
            <nuxt-link
              :to="{ name: 'movies-movieid', params: { movieid: popular.id } }"
            >
              <img
                :src="`https://image.tmdb.org/t/p/w400${popular.poster_path}`"
                alt=""
                width="w-full"
              />
            </nuxt-link>
          </div>
          <div class="">
            <nuxt-link
              :to="{ name: 'movies-movieid', params: { movieid: popular.id } }"
            >
              <h2 class="font-bold text-slate-700 text-lg text-center my-5">
                {{ popular.title }}
              </h2>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "IndexPage",
  data() {
    return {
      movies: [],
      popularMovies: [],
    };
  },
  async fetch() {
    this.movies = await fetch(
      "https://api.themoviedb.org/3/movie/now_playing?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1"
    )
      .then((res) => res.json())
      .then((data) => data.results);
    this.popularMovies = await fetch(
      "https://api.themoviedb.org/3/movie/popular?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1"
    )
      .then((res) => res.json())
      .then((data) => data.results);
  },

  // async asyncData({ params, $http }) {
  //   const movies = await axios.get(
  //     `https://api.themoviedb.org/3/movie/now_playing?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1`
  //   );
  //   const popularMovies = await axios.get(
  //     `https://api.themoviedb.org/3/movie/popular?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1`
  //   );

  //   return {
  //     movies: movies.data.results,
  //     popularMovies: popularMovies.data.results,
  //   };
  // },
};
</script>

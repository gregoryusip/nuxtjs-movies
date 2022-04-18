<template>
  <div class="container p-8">
    <div class="flex flex-wrap px-4">
      <div class="mb-10 px-4 w-full md:w-1/3 md:mb-0">
        <div class="rounded-lg shadow-md overflow-hidden">
          <img
            :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`"
            alt=""
            width="w-full"
          />
        </div>
      </div>

      <div class="mb-10 px-4 w-full md:w-2/3 md:mb-0">
        <h1 class="font-bold text-5xl text-slate-800 mb-5">
          {{ movie.title }}
        </h1>

        <div class="border-t-4 border-red-800 mb-5"></div>

        <h5 class="font-semibold text-xl text-slate-800 mb-2">Genres:</h5>
        <ul class="text-slate-300 mb-5">
          <li v-for="(genre, index) in movie.genres" :key="index">
            <a href="#" class="inline-block text-base hover:text-primary mb-2"
              >{{ index + 1 }}. {{ genre.name }}</a
            >
          </li>
        </ul>

        <h5 class="font-semibold text-xl text-slate-800 mb-2">Release Date:</h5>
        <p class="text-base mb-5">{{ movie.release_date }}</p>

        <h5 class="font-semibold text-xl text-slate-800 mb-2">Rate:</h5>
        <p class="text-base mb-5">{{ movie.vote_average }}</p>

        <h5 class="font-semibold text-xl text-slate-800 mb-2">Overview:</h5>
        <p class="text-base mb-10">{{ movie.overview }}</p>

        <nuxt-link to="/" class="px-6 py-3 bg-yellow-400 font-semibold text-md"
          >Back to Home</nuxt-link
        >
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "movie-detail",
  data() {
    return {
      movie: null,
    };
  },
  async asyncData({ params }) {
    // const movie = await axios.get(
    //   `https://api.themoviedb.org/3/movie/${params.movieid}?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1`
    // );
    // return { movie: movie.data };

    const movie = await fetch(
      `https://api.themoviedb.org/3/movie/${params.movieid}?api_key=2e0ec924191ee1585a8ddadf6b7f1d7a&language=en-US&page=1`
    )
      .then((res) => res.json())
      .then((data) => data);

    console.log(movie);

    return { movie };
  },
};
</script>

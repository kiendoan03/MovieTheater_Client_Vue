<script setup lang="ts">
import '../assets/css/home.css';
import { ref, onMounted } from 'vue';
// @ts-ignore
import initSlider from '../assets/js/home_slider.js';

onMounted(() => {
    // Chờ 1 khoảng thời gian ngắn sau khi component được mount để đảm bảo rằng các phần tử đã được render trong DOM
    setTimeout(() => {
        initSlider();
    }, 100);
});
</script>

<template>
  <main>
     <!-- movie selection-->

    <section class="movie_selection row mt-5">

        <div class="row justify-content-center mt-5">
            <div class="col-lg-7 col-md-8">
                <div class="text-center">
                    <h1 class="text-light" style="font-size: 2.5vmax; font-family: 'Poppins', sans-serif;">Movie Selection</h1>
                </div>
            </div>
        </div>

        <!-- Movie carousel -->

        <section class="p-0">
            <div class="slider col-12">
                <div v-for="movieShow in movie_show" :key="movieShow.id" class="mx-3">
                    <div class="card border-0 rounded-0 ">
                        <div class="d-flex bg-opacity-25 justify-content-center align-items-end">
                            <RouterLink :to="'/movieDetail/' + movieShow.id">
                                <img :src="movieShow.thumbnail" alt="">
                            </RouterLink>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </section>

    <!-- Top Movie -->

    <section class="top_movie">
        <div class="row justify-content-center mt-5">
            <div class="col-lg-7 col-md-8">
                <div class="text-center">
                    <h1 class="text-light " style="font-size: 2.5vmax; font-family: 'Poppins', sans-serif;">Top Movie</h1>
                </div>
            </div>
        </div>
        <div class="row mt-3">

            <div v-for="(topMovie, index) in top_movie" :key="topMovie.id" class="col-6 col-lg-3 mb-5">
                <div class="card image-container h-100">
                    <div class="background-image">
                        <div class="overlay-content">
                            <h1>{{ index + 1 }}</h1>
                        </div>
                    </div>
                    <RouterLink :to="'/movieDetail/' + topMovie.id">
                        <img :src="topMovie.poster" alt="Overlay Image" class="overlay-image">
                    </RouterLink>
                </div>
            </div>
        </div>

    </section>

    <!-- incomming -->

    <section class="incomming px-5">
        <div class="row justify-content-center mt-5">
            <div class="col-lg-7 col-md-8">
                <div class="text-center">
                    <h1 class="text-light " style="font-size: 2.5vmax; font-family: 'Poppins', sans-serif;">Upcomming Movie</h1>
                </div>
            </div>
        </div>

        <div class="row mt-3 mb-5">
            <div v-for="movieIncomming in movie_incomming" :key="movieIncomming.id" class="col-3 mb-5">
                <div class="card" style="width: 23vmax;">
                    <RouterLink :to="'/movieDetail/' + movieIncomming.id">
                        <img :src="movieIncomming.thumbnail" class="card-img-top object-fit-cover " style="opacity:0.9; border-radius :1vmax" alt="...">
                    </RouterLink>
                </div>
            </div>
        </div>

    </section>
  </main>
</template>
<script lang="ts">
import axios from 'axios';
  export default {
    name: 'HomeView',
    data(){
      return {
        movie_show: [],
        top_movie: [],
        movie_incomming: [],
        baseUrl: 'https://localhost:7071'
      }
    },
    mounted(){
      this.getMovieShow();
      this.getTopMovie();
      this.getMovieIncomming();
    },
    methods:{
      async getMovieShow(){
         await  axios.get('https://localhost:7071/api/Movies/get-movies-showing').then(response => {
            this.movie_show = response.data.map(movieShow => ({
              movieName: movieShow.movieName,
              id: movieShow.id,
              thumbnail: this.baseUrl + movieShow.thumbnail,
            }));
            console.log(this.movie_show);
        }).catch(error => {
            console.error('Error fetching movies:', error);
        });
      },
      async getTopMovie(){
        await axios.get('https://localhost:7071/api/movies/get-top-movies').then(response => {
          this.top_movie = response.data.map(topMovie  => ({
            movieName: topMovie.movieName,
            id: topMovie.id,
            poster: this.baseUrl + topMovie.poster,
          }));
          console.log(this.top_movie);
        }).catch(error => {
          console.error('Error fetching movies:', error);
        });
      },
      async getMovieIncomming(){
        await axios.get('https://localhost:7071/api/movies/get-movies-upcoming').then(response => {
          this.movie_incomming = response.data.map(movieIncomming  => ({
            movieName: movieIncomming.movieName,
            id: movieIncomming.id,
            thumbnail: this.baseUrl + movieIncomming.thumbnail,
          }));
          console.log(this.movie_incomming);
        }).catch(error => {
          console.error('Error fetching movies:', error);
        });
      }
    },
    }
</script>
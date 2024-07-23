<template>
    <section class="mt-5 pt-5 px-5">
      <div class="row">
        <div class="col-6">
          <span class="text-secondary" style="font-size: 0.8vmax;">Search</span>
            <div class="input-group mt-2">
              <input
                v-model="searchContent"
                type="text"
                name="search_content"
                style="background-color: rgb(75, 75, 75); border-radius: 1vmax ; color:#fff"
                class="form-control border-0 text-light shadow-none"
                placeholder="Search"
                @keydown.enter="searchMovies"
              />
            </div>
        </div>
        <div class="col-6">
          <div class="row">
              <div class="col-5 mx-2" style="float: left;">
                <span class="text-secondary" style="font-size: 0.8vmax;">Genre</span>
                <select
                  v-model="selectedGenre"
                  name="category"
                    @change="searchByGenre"
                  class="form-select form-select-sm mt-2 border-0 shadow-none text-light"
                  aria-label=".form-select-sm example"
                  style="background-color: rgb(75, 75, 75); border-radius: 1vmax; height: 1.82vmax; padding-left: 0.6vmax;"
                >
                  <option selected hidden>Genre</option>
                  <option v-for="genre in genres" :key="genre.id" :value="genre.id">
                    {{ genre.genreName }}
                  </option>
                </select>
              </div>
              <div class="col-5 text-center mx-2" style="line-height: 5.7; float:right">
                <button class="btn bg-danger w-100 text-light shadow-none" @click="searchMovies" type="submit" style="border-radius: 1vmax;">
                  Search
                </button>
              </div>
          </div>
        </div>
      </div>
    </section>
  
    <section>
      <div class="row mt-5 mb-5">
        <div v-if="movies.length" v-for="movie in movies" :key="movie.id" class="col-3 mb-5">
          <div class="card bg-transparent" style="width: 20vmax;">
            <RouterLink :to="`/movieDetail/${movie.id}`">
              <img
                :src="movie.poster"
                class="card-img-top object-fit-cover"
                style="opacity:0.9; border-radius :1vmax; box-shadow: #fff 0px 5px 15px; object-fit:cover;"
                alt="..."
              />
            </RouterLink>
          </div>
          <div class="card-body">
            <span class="card-text text-light" style="font-size: 1.3vmax;">{{ movie.movieName }}</span>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import axios from 'axios';
  export default {
    data() {
      return {
        searchContent: '',
        selectedGenre: '',
        genres: [],
        movies: [],
        baseUrl: 'https://localhost:7071',
      };
    },
    created() {
      this.fetchGenres();
    },
    methods: {
      searchMovies() {
        axios
          .get(`https://localhost:7071/api/Movies/get-movies-by-keywork?keyword=${this.searchContent}`)
          .then((response) => {
            this.movies = response.data;
            this.movies = this.movies.map((movie) => ({
              id: movie.id,
              movieName: movie.movieName,
              poster: this.baseUrl + movie.poster,
            }));
          })
          .catch((error) => {
            console.log(error);
          });
      },
      searchByGenre() {
        axios
          .get(`https://localhost:7071/api/Movies/get-movies-by-genre?genreId=${this.selectedGenre}`)
          .then((response) => {
            this.movies = response.data;
            this.movies = this.movies.map((movie) => ({
              id: movie.id,
              movieName: movie.movieName,
              poster: this.baseUrl + movie.poster,
            }));
          })
          .catch((error) => {
            console.log(error);
          });
      },
      fetchGenres() {
        axios
          .get('https://localhost:7071/api/Genres')
          .then((response) => {
            this.genres = response.data;
          })
          .catch((error) => {
            console.log(error);
          });
      },
    },
  };
  </script>
  
  <style scoped>
  </style>
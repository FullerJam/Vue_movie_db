<template>
  <div class="wrapper">
    <ul>
      <li v-for="movie in movies">
        <Movie :movie="movie"/>
      </li>
    </ul>
  </div>
</template>
c

<script>
import Movie from "./Movie.vue";
export default {
  name: "MoviesList",
  data() {
    return {
      movies: []
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const apiresult = await fetch(
          "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=61f5be92f883e17ccd79d16d4f107a1b"
        );
        const movies = await apiresult.json();
        this.movies = movies.results;
      } catch (e) {
        console.log(e);
      }
    }
  },
  components: {
    Movie
  }
};
</script>

<style scoped>
ul {
  display: grid;
  list-style: none;
  padding: 2rem;
  margin: 0;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(6, 1fr);
}
.wrapper {
    width: 70%;
    margin:0 auto;
}
img:hover{
    box-shadow: 0px 0px 10px 10px #0ff;
    /* in order: x offset, y offset, blur size, spread size, color */
    transform: all 5s ease;
}
</style>
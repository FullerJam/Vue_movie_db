<template>
  <div class="movie-card" :style="styles">
    <div class="title">
      <h1>{{ movie.title }}</h1>
      <h3>{{movie.release_date}}</h3>
    </div>
    <div class="movie-info">
      <p>{{movie.overview}}</p>
    </div>
  </div>
</template>

<script>
const BACKDROP_PATH = "http://image.tmdb.org/t/p/w1280";
export default {
  data() {
    return {
      movie: {}
    };
  },
  created: function() {
    //when .doc is ready run this.fetchdata
    this.fetchData();
  },
  computed: {
    styles() {
      return {
        background: `url(${BACKDROP_PATH}/${
          this.movie.backdrop_path
        }) no-repeat`
      };
    }
  },
  methods: {
    fetchData: async function() {
      try {
        const apiresult = await fetch(
          `https://api.themoviedb.org/3/movie/${
            this.$route.params.id
          }?api_key=61f5be92f883e17ccd79d16d4f107a1b` 
        );
        const movie = await apiresult.json();
        this.movie = movie;
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>

<style scoped>
h1 {
  color: #222;
}

.movie-card {
  position: relative;
  padding-top: 40vh;
  background-size: cover;
  margin: 0 auto;
  width: 50%;
  border-radius: 10px;
}
.movie-info {
  background: white;
  color: #222;
  padding: 2rem 10%;
  margin-top: 6rem;
  border-radius: 0 0 10px 10px;
}
.title {
    position: absolute;
  padding: 0;
  background-color: #222;
  width: 100%;
  vertical-align: bottom;
}
.title,
h1 {
  color: aliceblue;
  padding:0;
}

</style>
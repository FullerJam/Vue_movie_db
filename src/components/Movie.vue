<template>
    <div>
        <router-link :to="moviePath">
            <img :src="posterImage" :alt="movie.title"/>
        </router-link>
    </div>
</template>

<script>
    const POSTER_PATH = "http://image.tmdb.org/t/p/w154"
    export default {
        props: ['movie'],
        computed: {
            posterImage: function() {
                return `${POSTER_PATH}/${this.movie.poster_path}`;
            },
            moviePath: function(){
                return `/movie/${this.movie.id}`;
            }
        }
    };

</script>

<style scoped>
    img{
        box-shadow: 0 0 35px black;
        transition: all .15s ease-in-out
    }
    img:hover{
    box-shadow: 0px 0px 10px 10px #0ff;
    /* in order: x offset, y offset, blur size, spread size, color */
    transform: scale(1.1);
}
    
</style>
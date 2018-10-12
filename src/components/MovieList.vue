<template>
    <div id="movie-list">
        <div v-for="movie in filteredMovies" class="movie">{{ movie.title }}</div>
    </div>
</template>
<script>
    import genres from '../util/genres';
    
    export default {
    data: function () {
            return {
                movies: [
                    { title: 'Star Wars', genre: genres.DRAMA },
                    { title: 'Scarface', genre: genres.CRIME },
                    { title: 'The Godfather', genre: genres.CRIME }
                ]
            }
        },
        props: [
            'genre', 'time'
        ],
        methods: {
            moviePassesGenreFilter(movie) {
                if (!this.genre.length) {
                    return true;
                } else {
                    return this.genre.find(genre => movie.genre === genre);
                }
            }
        },
        computed: {
            filteredMovies() {
                return this.movies.filter(this.moviePassesGenreFilter);
            }
        }
    }
</script>
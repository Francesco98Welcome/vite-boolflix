<script>
import { store } from '../store.js';
export default {
    name: 'AppMain',
    data() {
        return {
            store
        }
    },
}
</script>

<template>
    <main>
        <div class="filmAndSerie">
            <div v-for="film in store.films" class="Movies">
                <div>
                    <img :src="'https://image.tmdb.org/t/p/w200' + film.poster_path" alt="">
                    <!--{{ film.title }}
                    {{ film.original_title }}
                    {{ film.original_language }}
                    {{ film.vote_average }}-->
                </div>
            </div>

            <div v-for="serie in store.series" class="Series">
                <div>
                    <img :src="'https://image.tmdb.org/t/p/w200' + serie.poster_path" alt="">
                    <!--{{ serie.title }}
                            {{ serie.original_title }}
                            {{ serie.original_language }}
                            {{ serie.vote_average }}-->
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss">
main {
    padding-top: 14px;
    /*background-image: url('../assets/sfondoNetflix.jpeg');
    background-size: contain;
    background-repeat: no-repeat;*/
}

.filmAndSerie {
    width: 90%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    background-color: black;

    .Movies,
    .Series>div {
        margin: 0 auto;
        padding: 2px;
    }
}
</style>
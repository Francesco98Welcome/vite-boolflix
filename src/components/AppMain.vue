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
                    <div class="image">
                        <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt="">
                    </div>
                    <div class="info-film">
                        <div class="title-lang-vote">
                            <div><span>Titolo:</span> {{ film.title }}</div>
                            <div><span>Titolo originale:</span> {{ film.original_title }}</div>
                            <div><span>Lang:</span> {{ film.original_language }}</div>
                            <div><span>Voto:</span> {{ film.vote_average }}</div>
                        </div>
                    </div>
                </div>
            </div>

            <div v-for="serie in store.series" class="Series">
                <div>
                    <div class="image">
                        <img :src="'https://image.tmdb.org/t/p/w300' + serie.poster_path" alt="">
                    </div>
                    <div class="info-film">
                        <div class="title-lang-vote">
                            <div><span>Titolo:</span> {{ serie.title }}</div>
                            <div><span>Titolo originale:</span> {{ serie.original_title }}</div>
                            <div><span>Lang:</span> {{ serie.original_language }}</div>
                            <div><span>Voto:</span> {{ serie.vote_average }}</div>
                        </div>
                    </div>
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
    background-color: lightgray;

    .Movies,
    .Series>div {
        margin: 0 auto;
        padding: 2px;

        &:hover .info-film {
            display: block;
            cursor: pointer;
        }
    }

    .Movies,
    .Series {
        position: relative;

        .info-film {
            width: 300px;
            height: 450px;
            background-color: rgba(0, 0, 0, 0.8);
            position: absolute;
            bottom: 1%;
            padding: 50px;
            color: white;
            line-height: 2;
            display: none;
            font-size: 17px;

            img {
                width: 50px;
            }
        }
    }

    span {
        color: red;
    }
}
</style>
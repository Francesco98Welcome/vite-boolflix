<script>
import { store } from '../store.js';
export default {
    name: 'AppMain',
    data() {
        return {
            store
        }
    },
    methods: {
        getFlag(lang) {
            switch (lang) {
                case 'en':
                    lang = 'uk';
                    break;
                case 'pt':
                    lang = 'po';
                    break;
                case 'es':
                    lang = 'sp';
                    break;
            }

            const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;

            return flag;
        },
        getVoteFilm(film) {
            let newVoteFilm = film.vote_average;
            newVoteFilm = newVoteFilm / 2;
            newVoteFilm = Math.ceil(newVoteFilm); //arrotondo per eccesso
            console.log('FILM', film.title, ':', film.vote_average, '-', newVoteFilm);
            return newVoteFilm;
        },
        getVoteSerie(serie) {
            let newVoteSerie = serie.vote_average;
            newVoteSerie = newVoteSerie / 2;
            newVoteSerie = Math.ceil(newVoteSerie);
            console.log('SERIE', serie.name, ':', serie.vote_average, '-', newVoteSerie);
            return newVoteSerie;
        }

    }
}
</script>

<template>
    <main>

        <div class="title">
            Film e serie TV , solo su BoolFlix
        </div>
        <div class="filmAndSerie">
            <div v-for="film in store.films" class="Movies">
                <div>
                    <div class="image">
                        <img :src="'https://image.tmdb.org/t/p/w300' + film.poster_path" alt="">
                    </div>
                    <div class="info-film-serie">
                        <div class="title-lang-vote">
                            <div><span>Titolo:</span> {{ film.title }}</div>
                            <div><span>Titolo originale:</span> {{ film.original_title }}</div>
                            <div><span>Lang:</span>
                                <!--{{ film.original_language }}-->
                                <img :src="getFlag(film.original_language)" class="flag">
                            </div>
                            <div>
                                <span>Voto:</span>
                                <span class="starOn" v-for="star in getVoteFilm(film)">★</span>
                                <span class="starOff" v-for="stars in (5 - getVoteFilm(film))">☆</span>
                                <!-- {{ film.vote_average }}-->
                                <!--{{ getVoteFilm(film) }}-->
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div v-for="serie in store.series" class="Series">
                <div>
                    <div class="image">
                        <img :src="'https://image.tmdb.org/t/p/w300' + serie.poster_path" alt="">
                    </div>
                    <div class="info-film-serie">
                        <div class="title-lang-vote">
                            <div><span>Titolo:</span> {{ serie.name }}</div>
                            <div><span>Titolo originale:</span> {{ serie.original_name }}</div>
                            <div><span>Lang:</span>
                                <img :src="getFlag(serie.original_language)" class="flag">
                            </div>
                            <div>
                                <span>Voto:</span>
                                <span class="starOn" v-for="star in getVoteSerie(serie)">★</span>
                                <span class="starOff" v-for="stars in (5 - getVoteSerie(serie))">☆</span>
                                <!-- {{ serie.vote_average }}-->
                                <!-- {{ getVoteSerie(serie) }} -->
                            </div>
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

    .title {
        text-align: center;
        font-size: 22px;
        color: red;
        padding: 20px;

    }
}

.filmAndSerie {
    width: 90%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    background-color: rgb(0, 0, 0);

    .Movies,
    .Series>div {
        margin: 0 auto;
        padding: 3px;

        &:hover .info-film-serie {
            display: block;
            cursor: pointer;
            opacity: 1;
            //display: block;
            transition: 1s;
        }
    }

    .Movies,
    .Series {
        position: relative;

        .info-film-serie {
            width: 300px;
            height: 455px;
            background-color: rgba(0, 0, 0, 0.86);
            position: absolute;
            bottom: 1%;
            padding: 40px;
            color: white;
            line-height: 2;
            font-size: 19px;
            opacity: 0;

            img {
                width: 50px;
            }
        }

    }

    span {
        color: red;
        text-decoration: underline;
    }

    .starOn {
        color: gold;
        margin-left: 10px;
        text-decoration: none;
    }

    .starOff {
        margin-left: 10px;
        color: white;
        text-decoration: none;
    }
}
</style>
<script>
import { store } from '../store.js';
import "@fortawesome/fontawesome-free/css/all.css";


export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    },
    emits: [
        'performSearch',
    ]
}
</script>

<template>
    <header>
        <div>
            <a href="#">
                <img src="https://github.com/carlosavilae/Netflix-Clone/blob/master/img/logo.PNG?raw=true">
            </a>
            <div class="links">
                <a href="#">Home </a>
                <a href="#">Serie TV</a>
                <a href="#">Film</a>
                <a href="#">Originali</a>
                <a href="#">Aggiunti di recente</a>
                <a href="#">La mia lista</a>
            </div>
        </div>
        <div>
            <span class="icon-input">
                <span class="icon-search"><i class="fa-solid fa-magnifying-glass"></i></span>
                <input type="text" v-model="store.searchText" v-on:keyup.enter="$emit('performSearch')"
                    placeholder="Cerca qualcosa..">
            </span>
            <button type="submit" @click="$emit('performSearch')">Search</button>
        </div>
    </header>
</template>

<style lang="scss">
header {
    padding: 20px;
    background-color: rgb(0, 0, 0);
    display: flex;
    align-items: center;
    justify-content: space-between;

    >div:first-child {
        color: red;
        font-size: 22px;
        display: flex;
        align-items: center;

        .links {
            margin-left: 20px;

            >a {
                color: white;
                text-decoration: none;
                padding-left: 10px;
                font-size: 15px;

                &:hover {
                    color: rgb(152, 49, 49);
                    transition: 2s;
                }
            }
        }
    }

    >div:last-child {
        margin-right: 50px;
    }

    .icon-input {
        border: 1px solid lightgray;
        padding: 6px;
        background-color: black;
        border-radius: 4px;
        margin-right: 20px;
        border: 1px solid white;
        border-radius: 8px;

        >input {
            background-color: black;
            color: lightgray;
            border: none;
            margin-left: 4px;
            padding: 6px;
        }

        >.icon-search {
            color: white;
            font-size: 14px;
        }
    }

    button {
        padding: 6px;
        border-radius: 4px;
        border: none;

        &:hover {
            color: white;
            background-color: black;
            border: 1px solid white;
            cursor: pointer;
            transition: 2s;
        }
    }
}
</style>
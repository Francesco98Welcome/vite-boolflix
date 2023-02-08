<script>
import { store } from '../store.js';

export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    },
    emits: [
        'search'
    ]
}
</script>

<template>
    <header>
        <div>
            BOOLFLIX
        </div>
        <div>
            <input type="text" v-model="store.searchText" placeholder="Cerca qualcosa..">
            <button type="submit" @click="$emit('search')">Search</button>
        </div>
    </header>
</template>

<style lang="scss">
header {
    padding: 20px;
    background-color: black;
    display: flex;
    align-items: center;
    justify-content: space-between;

    >div:first-child {
        color: red;
        font-size: 22px;

    }

    >div:last-child>input {
        margin-right: 30px;
        padding: 6px;
    }

    >div:last-child>button {
        padding: 6px;
    }
}
</style>
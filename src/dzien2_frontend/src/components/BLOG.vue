<template>
    <div>
        <h2 class="text-blue-600"></h2>
        <button @click="Pobierz Wpisy">refresh</button>
        <div v-for="wpis in wpisy">
                siema blog!
        {{ wpisy }}
        </div>
        <input> v-model="nowyBlog" type="text">
        <button @click="dodajwpisy">dodaj</button>
        {{ nowyBlog }}
    </div>
</template>

<script>
import {dzien2_backend } from 'declarations/dzien2_backend/index'

export default {
    data() {
        return{
            wpisy: []
        }
    },
    methods: {
        async dodajWpisy(){
           await dzien2_backend.dodaj_Wpisy(nowyBlog);
        },
        async pobierzWpisy() {
           this.wpisy = await dzien2_backend.odczytaj_wpisy()

        }
    },
    async mounted() {
  this.pobierzWpisy();
}
}
</script>
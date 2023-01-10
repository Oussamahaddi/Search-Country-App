
<template>
    <!-- header  -->
    <div class=" flex items-center justify-between px-4 mb-10 bg-gradient-to-r from-gray-700 via-gray-900 to-black py-4">
        <img src="../assets/img/map.webp" alt="" class="w-[60px]">
        <div class="flex items-center gap-2">
            <input type="text" v-model="searchCountry" placeholder="search for city" class="outline-none border-2 border-blue-500 px-2 py-1 rounded-lg"><i class="fa-solid fa-magnifying-glass cursor-pointer" @click="show"></i>
        </div>
    </div>

    <!-- country -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 place-items-center gap-12">
        <div v-for="(pay, index) in search" :key="index" class="w-5/6 grid gap-2">
            <img :src="pay.flags" alt="" class="">
            <h1 class="text-center font-semibold text-lg">{{ pay.name }}</h1>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name : 'countries',
    
    data() {
        return {
            pays: null,
            searchCountry : '',
            CountryName : [],
        }
    },
    mounted() {
        axios
            .get('https://restcountries.com/v3.1/all')
            .then((response) => {
                this.pays = response.data;
                for (let i = 0; i < this.pays.length; i++) {
                    // put name and img inside varibale
                    let payObj = {
                        name : this.pays[i].translations.fra.common, 
                        flags : this.pays[i].flags.png
                    }
                    // push the object inside array
                    this.CountryName.push(payObj);
                }
                console.log(this.CountryName);
            });
    },

    computed: {
        search() {
            let search = new RegExp(this.searchCountry, 'i');

            return this.CountryName.filter(el => {
                return el.name.match(search);
            })
        }
    }
}


</script>
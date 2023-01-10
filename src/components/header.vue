
<template>
    <div class=" flex items-center justify-between px-2">
        <img src="../assets/img/map.webp" alt="" class="w-[80px]">
        <div class="flex items-center gap-2">
            <input type="text" v-model="search" placeholder="search for city" class="outline-none border-2 border-blue-500 px-2 py-1 rounded-lg"><i class="fa-solid fa-magnifying-glass cursor-pointer" @click="show"></i>
        </div>
    </div>
</template>

<script>
    export default {
        name : 'header',
        pay : '',

        computed: {
            search() {
                this.pay = ''
            }
        }
    }
</script>
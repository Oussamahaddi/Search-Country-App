<script>
//import components
import Header from './components/header.vue'
import Footer from './components/footer.vue'
import Country from './components/countries.vue'

export default {
  name: 'App',

  components: {
    Header,
    Country,
    Footer,
  }
}

</script>

<template>
  <div class="bg-gray-200">
    <Country />
  </div>
</template>

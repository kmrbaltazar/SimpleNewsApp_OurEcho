<script setup>
import Header from './components/home_components/Header.vue'
import SearchBar from './components/home_components/SearchBar.vue'
</script>

<template>
<Header />
<main>
<h1>Get access to top news globally</h1>
<SearchBar />
</main>

</template>

<style scoped>
h1 {
  color: #006297;
  font-size: 21px;
}

main {
  margin: 20px;
}

</style>

<script>
export default {
  data(){ // return part of data() is where we declare variables
    return{ // declare variables below and separate them with comma ,

    } // end of variable declaration area
  }
}
</script>
<script setup>
import Header from "./components/home_components/Header.vue";
import SearchBar from "./components/home_components/SearchBar.vue";
import Button from "./components/home_components/Button.vue";
</script>

<template>
  <Header />
  <main>
    <section class="home_section">
      <h1>Get access to top news globally</h1>
      <SearchBar />
      <div class="news_categories_grid">
        <Button
          v-for="category in news_top_categories"
          :Button_prop="category"
        />
      </div>
    </section>
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

.home_section {
  display: flex;
  flex-direction: column;
  gap: 20px;
  text-align: center;
}

.news_categories_grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: minmax(50px,auto);
  gap: 20px;
}
</style>

<script>
export default {
  data() {
    // return part of data() is where we declare variables
    return {
      // declare variables below and separate them with comma ,
      news_top_categories: [
        "Government",
        "Politics",
        "Economy",
        "Environment",
        "Business",
        "Technology",
        "Fashion",
        "Sports",
        "Entertainment",
      ],
    }; // end of variable declaration area
  },
};
</script>

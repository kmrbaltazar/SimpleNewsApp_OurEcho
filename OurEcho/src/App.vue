<script setup>
import Header from "./components/home_components/Header.vue";
import SearchBar from "./components/home_components/SearchBar.vue";
import Button from "./components/home_components/Button.vue";
import Footer from "./components/home_components/Footer.vue";
import NewsArticles from './components/NewsArticles.vue';
import ScrollMenu from './components/home_components/Scrolling_NewsCategories.vue';
import SearchKeywordDisplay from './components/home_components/SearchKeyword_display.vue'
</script>

<template>
<div class="fixed">
  <Header />
  <section class="news_section">
  <SearchKeywordDisplay />
  </section>
  </div>
  <main>
    <section class="home_section">
      <h1>Get access to top news globally</h1>
      <SearchBar @searchclick="data_fetch" @searchvalue="query" />
      <div class="news_categories_grid">
        <Button v-for="category in news_top_categories" :Button_prop="category" />
      </div>
    </section>
    <section class="news_section">
      <NewsArticles v-for="(articles,index) in newsAPI_data_array" :Articles_prop="articles" :key="index" />
    </section>
  </main>
  <Footer />
</template>

<style scoped>
h1 {
  color: #006297;
  font-size: 21px;
}

main {
  margin: 130px 10px 0 10px;
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
  grid-auto-rows: minmax(50px, auto);
  gap: 15px;
}

.fixed{
  width: 100%;
  position: fixed;
  top: 0;
  z-index: 10;
  
}
</style>

<script>
export default {
  data() {
    return {
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
      newsAPI_data_array: [],
      my_boolean: false,
      query: ""
    }; 
  },

  methods:{ 
    async data_fetch(){
      const response = await fetch("https://newsapi.org/v2/everything?q="+this.query+"&apiKey=1c6df44b32f64dc1866e9dab4d670ce8");
      const received_data = await response.json();
      this.newsAPI_data_array = received_data.articles;
    }
  }, 

  created(){ 
    // this.data_fetch();
  } 
};
</script>

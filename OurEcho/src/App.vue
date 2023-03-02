<script setup>
import Header from "./components/home_components/Header.vue";
import SearchBar from "./components/home_components/SearchBar.vue";
import Button from "./components/home_components/Button.vue";
import Footer from "./components/home_components/Footer.vue";
import NewsArticles from "./components/NewsArticles.vue";
import ScrollMenu from "./components/home_components/Scrolling_NewsCategories.vue";
import SearchKeywordDisplay from "./components/home_components/SearchKeyword_display.vue";
import Loading from "./components/Loading.vue";
</script>

<template>
  <div class="fixed">
    <Header />
    <SearchKeywordDisplay :Keyword_prop="query" />
  </div>
  <section class="main-grid">
    <main>
      <section class="home_section" v-if="no_fetch_yet">
        <h1>Get access to top news globally</h1>
        <SearchBar @searchclick="get_searchinput" />
        <div class="news_categories_grid">
          <Button
            v-for="category in news_top_categories"
            :Button_prop="category"
            @click="get_searchinput(category)"
          />
        </div>
      </section>

      <Loading v-if="!no_fetch_yet && !newsAPI_data_array.length" />

      <NewsArticles
        v-for="(articles, index) in newsAPI_data_array"
        :Articles_prop="articles"
        :key="index"
      />
    </main>
    <Footer />
  </section>
</template>

<style scoped>
.main-grid {
  display: grid;
  grid-template-rows: 1fr auto;
  min-height: 100vh;
}

h1 {
  color: #006297;
  font-size: 21px;
}

main {
  margin: 140px 10px 0 10px;
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

.fixed {
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
      no_fetch_yet: true,
      query: "",
    };
  },

  methods: {
    async data_fetch() {
      const response = await fetch(
        "https://newsapi.org/v2/everything?q=" +
          this.query +
          "&apiKey=1c6df44b32f64dc1866e9dab4d670ce8"
      );
      const received_data = await response.json();
      this.newsAPI_data_array = received_data.articles;
    },
    get_searchinput(input_val) {
      this.query = input_val;
      this.data_fetch();
      this.no_fetch_yet = false;
    },
  },

  created() {
    // this.data_fetch();
  },
};
</script>

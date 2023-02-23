<script setup>
import Header from "./components/home_components/Header.vue";
import Footer from "./components/home_components/Footer.vue";
import NewsArticles from "./components/NewsArticles.vue";
</script>

<template>
  <div class="fixed">
    <Header />
    <section class="news_section">
      <!-- Search keyword display -->
      <div class="search_keyword_wrapper">
        <h4>Search:</h4>
        <p><a href="">Go back</a></p>
      </div>
    </section>
  </div>
  <main>
    <section class="home_section" :class="{other_main_class:my_boolean}">
      <h1>Get access to top news globally</h1>
      <div class="search_bar">
        <div class="input_div">
          <input type="text" placeholder="Enter search keyword" v-model="query" />
          <div class="searchicon_wrapper" @click="data_fetch" >
            <img src="@/assets/icons/search_icon.svg" alt="Search icon" />
          </div>
        </div>
      </div>
      <div class="news_categories_grid">
        <!-- Button -->
        <div class="button_wrapper" v-for="category in news_top_categories">
          <p>{{ category }}</p>
        </div>
      </div>
    </section>
    <section class="news_section">
      <div
        class="news_card_wrapper"
        v-for="(articles, index) in newsAPI_data_array"
        :key="index">
        <div class="news_text">
          <h4>{{ articles.title }}</h4>
          <p class="news_author">
            by {{ articles.author
            }}<span v-if="!articles.author">Anonymous</span>
          </p>
        </div>
        <div class="news_img_wrapper">
          <img :src="articles.urlToImage" alt="News Article Image" />
        </div>
      </div>
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

.other_main_class {
  margin-top: 90px !important;
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

/* Search keyword wrapper */
.search_keyword_wrapper {
  box-shadow: 0px 5px 4px rgba(0, 0, 0, 0.25);
  height: 50px;
  color: #616161;
  padding: 10px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #fff;
}

.search_keyword_wrapper a {
  color: #56b7ec;
}

/* Search bar */
.input_div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #757575;
  border-radius: 10px;
  height: 40px;
  padding: 0 10px;
}

.input_div input {
  border: none;
  height: 35px;
}

.input_div input:focus {
  outline: none;
}

/* Button wrapper */
.button_wrapper {
  background: linear-gradient(
    180deg,
    rgba(86, 183, 236, 1) 0%,
    rgba(0, 98, 151, 1) 100%
  );
  border-radius: 10px;
  height: 45px;
  color: #fff;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* News Card wrapper */
.news_card_wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  gap: 5px;
  z-index: 1;
}

.news_text {
  flex: 1.5;
}

.news_img_wrapper {
  flex: 1;
  height: 100px;
}

.news_text p {
  font-size: 12px;
  margin-top: 5px;
  font-style: italic;
}

.news_text h4 {
  color: #006297;
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
      query: "",
    };
  },

  methods: {
    async data_fetch() {
      const response = await fetch(
        'https://newsapi.org/v2/everything?q='+this.query+'&apiKey=1c6df44b32f64dc1866e9dab4d670ce8'
      );
      const received_data = await response.json();
      this.newsAPI_data_array = received_data.articles;
      console.log(this.newsAPI_data_array);
    },
  },

  created() {
    // this.data_fetch();
  },
};
</script>

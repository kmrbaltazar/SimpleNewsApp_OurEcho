<template>
    <div class="news_card_wrapper">
        <div class="news_text">
            <h4>{{Articles_prop.title}}</h4>
            <!-- <p class="news_url">{{Articles_prop.url}}</p> -->
            <p class="news_author">by {{Articles_prop.author}}<span v-if="!Articles_prop.author.length">Anonymous</span></p>
        </div>
        <div class="news_img_wrapper">
            <img :src="Articles_prop.urlToImage" alt="News Article Image">
        </div>
    </div>
</template>

<style scoped>
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
    height: 90px;
}

p {
    font-size: 12px;
    margin-top: 5px;
    font-style: italic;
}

h4 {
    color: #006297;
}
</style>

<script setup>
defineProps({
  Articles_prop: {
    // Change 'PropName' to your choice of variable name and match it in the component that is sending the prop value
    type: Object, //Change to the type of prop variable you plan to receive e.g. String, Number, Array, Object, Boolean
    required: true,
  }
}); // end of defineProps

</script>
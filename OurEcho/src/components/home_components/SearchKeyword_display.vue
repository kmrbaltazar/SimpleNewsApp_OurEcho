<template>
    <div class="search_keyword_wrapper">
        <h4>Search: {{Keyword_prop}}</h4>
        <p><a href="">Reset</a></p>
    </div>
</template>

<style scoped>
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

a {
    color: #56B7EC;
}

@media (min-width: 63em) {
    .search_keyword_wrapper {
        width: 40%;
    }
}
</style>

<script setup>
defineProps({
  Keyword_prop: {
    // Change 'PropName' to your choice of variable name and match it in the component that is sending the prop value
    type: String, //Change to the type of prop variable you plan to receive e.g. String, Number, Array, Object, Boolean
    required: true,
  }
}); // end of defineProps
</script>
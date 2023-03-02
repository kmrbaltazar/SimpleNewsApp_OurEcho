<template>
  <section class="input_section">
    <div class="input_div">
      <input
        type="text"
        placeholder="Enter search keyword"
        v-model="search_value"
      />
      <div class="searchicon_wrapper" @click="search_clicked">
        <img src="@/assets/icons/search_icon.svg" alt="Search icon" />
      </div>
    </div>
    <span v-if="warning">
      <p class="no_input_value_p" >
        <sup>*</sup>Please enter a keyword or click on a topic below
      </p>
    </span>
  </section>
</template>

<style scoped>
.input_div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #757575;
  border-radius: 10px;
  height: 40px;
  padding: 0 10px;
}

input {
  border: none;
  height: 35px;
}

input:focus {
  outline: none;
}

img {
  filter: drop-shadow(2px 2px 2px grey);
}

.no_input_value_p {
  color: red;
  font-style: italic;
  font-size: 12px;
  text-align: left;
}
</style>

<script>
export default {
  data() {
    return {
      search_value: "",
      warning: false
    };
  },
  methods: {
    search_clicked() {
      this.warning = false;
      if (this.search_value.length) 
        this.$emit("searchclick",this.search_value);
      else
        this.warning = true;
    },
  },
  emits: ["searchclick"],
};
</script>

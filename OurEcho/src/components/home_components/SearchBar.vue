<template>
  <div class="input_div">
    <input type="text" placeholder="Enter search keyword" v-model="$emit('searchvalue')" />
    <div class="searchicon_wrapper" @click="$emit('searchclick')">
      <img src="@/assets/icons/search_icon.svg" alt="Search icon" />
    </div>
  </div>
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

</style>

<script>
export default {
  data(){
    return {

    }
  },
  methods: {

  },
  emits:['searchvalue','searchclick']
}
</script>

<template>
  <div class="button_wrapper">
    <p>{{ Button_prop }}</p>
  </div>
</template>

<style scoped>
.button_wrapper {
  background: linear-gradient(180deg, rgba(86,183,236,1) 0%, rgba(0,98,151,1) 100%);
  border-radius: 10px;
  height: 45px;
  color: #fff;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

<script setup>
defineProps({
  Button_prop: {
    // Change 'PropName' to your choice of variable name and match it in the component that is sending the prop value
    type: Array, //Change to the type of prop variable you plan to receive e.g. String, Number, Array, Object, Boolean
    required: true,
  },
  SingleButton_prop: {
    type: String,
    required: true,
  }
}); // end of defineProps
</script>

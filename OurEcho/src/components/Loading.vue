<template>
<section class="loading_section">
<h1>LOADING ARTICLES</h1>
    <div class="loader"></div>
</section>
    
</template>

<style scoped>
.loading_section {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 30px;
}

  .loader {
  border: 16px solid #f3f3f3; /* Light grey */
  border-top: 16px solid #3498db; /* Blue */
  border-radius: 50%;
  width: 120px;
  height: 120px;
  animation: spin 5s linear infinite;
}  

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
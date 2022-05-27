<script setup lang="ts">
import { ref } from "vue";

const {data:api} = await useFetch('/api/hello');
const info = ref(api);
</script>
<template>
  <div>
    <Title>Nuxt 3 Learning</Title>
    <div class="container">
          <h1>Welcome to Restaurantly</h1>
             <Products />
          <NuxtLink to="/shop">Go to restaurants</NuxtLink>
       
        </div>
  </div>
</template>
<style scoped>
.container{
  margin-top: 5rem;
}


</style>

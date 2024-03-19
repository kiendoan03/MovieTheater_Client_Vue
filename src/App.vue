<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HeaderView from './components/HeaderView.vue';
</script>

<template>
    
    <header class="row d-flex fixed-top p-3 justify-content-between" style="background-color:none">
      <HeaderView />
    </header>

  <RouterView />
</template>

<style scoped>

</style>

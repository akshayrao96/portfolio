<template>
  <div class="bg-[#111827] min-h-screen">
    <NavBar />
  </div>
  <HeroSection />
</template>

<script setup>
  import { defineAsyncComponent } from 'vue';
  // Impor Components Asynchronously
  const NavBar = defineAsyncComponent(() => import('@/components/NavBar.vue'));
</script>

<script setup lang="ts">
import { RouterView } from 'vue-router'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div id="app" class="min-h-screen bg-white">
    <Navbar />
    <main class="pt-16">
      <RouterView />
    </main>
    <Footer />
  </div>
</template>

<style>
/* 全局样式已在 main.css 中定义 */
</style>

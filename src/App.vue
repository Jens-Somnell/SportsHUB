<template>
  <div id="app">
    <Navbar />
    <RouterView />
    <Footer footerText="SportsHUB" />
  </div>
</template>

<script setup>
import './assets/styles.css'
import Navbar from './components/NavbarComponent.vue'
import Footer from './components/FooterComponent.vue'
import { RouterView } from 'vue-router'
</script>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';
</script>

<template>
  <header>
    <!-- Logo enlevé et collé dans NAVBAR.VUE
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->
    <Navbar/>

    <!-- <div class="wrapper"> -->
      <!-- <HelloWorld msg="You did it!" /> -->

      <!-- <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/portfolio">Portfolio</RouterLink>
      </nav>
    </div> -->
  </header>

  <RouterView />
  <!-- <HelloWorld msg="Camille" />
  <HelloWorld msg="Stef" />
  <HelloWorld msg="Morgan" /> -->

  <Footer />
</template>
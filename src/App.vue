<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import AnimatedComponent from "@/components/AnimatedComponent.vue";
</script>

<template>
  <!--<header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>


    </div>
    <div class="container">

    </div>
  </header>-->
  <Transition v-if="showMenu">
  <header
    class="menu d-flex flex-wrap align-items-center justify-content-center justify-content-md-between mb-4 border-bottom p-3 text-bg-dark"
  >
    <a href="/" class="d-flex">
      <img alt="AVV Services" class="logo" src="@/assets/logo.svg" />
    </a>

    <!--<ul class="nav col-12 col-md-auto mb-2 justify-content-center mb-md-0">
        <li><a href="#" class="nav-link px-2 link-secondary">Home</a></li>
        <li><a href="#" class="nav-link px-2 link-dark">Features</a></li>
        <li><a href="#" class="nav-link px-2 link-dark">Pricing</a></li>
        <li><a href="#" class="nav-link px-2 link-dark">FAQs</a></li>
        <li><a href="#" class="nav-link px-2 link-dark">About</a></li>
      </ul>-->

    <nav class="nav col-12 col-md-auto mb-2 justify-content-center mb-md-0">
      <RouterLink class="nav-link px-2 link-dark" to="/">Home</RouterLink>
      <RouterLink class="nav-link px-2 link-dark" to="/about">About</RouterLink>
    </nav>

    <div class="col-md-3 text-end">
      <button type="button" class="btn btn-outline-primary me-2">Login</button>
      <button type="button" class="btn btn-primary">Sign-up</button>
    </div>
  </header>
  </Transition>


  <RouterView />
</template>

<style scoped>
@import "./styles/base.scss";
</style>

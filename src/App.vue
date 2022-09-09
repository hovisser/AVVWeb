<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HeaderComponent from "@/components/header/HeaderComponent.vue";
</script>

<template>
  <HeaderComponent />
  <RouterView />
</template>

<style scoped>
@import "@/styles/base.scss";
</style>

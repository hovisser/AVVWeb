<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { ref } from "vue";
</script>

<template>
  <RouterView />
</template>

<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.6s ease-in;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

</style>

<script lang="ts" setup>
import { onMounted, ref, computed, defineProps, defineComponent } from "vue";

const props = defineProps({
  animationType:  {
      type: String,
      required: false,
      default: "fade",
  },
});

const target = ref();
const animate = ref(false);

const observer = new IntersectionObserver(
      (entries: IntersectionObserverEntry[]) => {
        entries.forEach((entry) => {
          if(entry.target.id === target.value.id) {
            animate.value = entry.isIntersecting;                                
          }
           
        });
      },
      {
        threshold: 0,
      }
);

onMounted(() => {
      observer.observe(target.value);
 });
</script>

<template>
  <div ref="target">
    <transition :name="animationType">
      <div v-if="animate" class="animated-component">
        <slot />
      </div>
    </transition>
  </div>
</template>

<style scoped>
.animated-component.fade-enter-from,
.animated-component.zoom-enter-from {
  transition: none;
}
/* Fade animation */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 300ms ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
/* Zoom animation */
.zoom-enter-active,
.zoom-leave-active {
  transition: transform 300ms ease;
}
.zoom-enter-from,
.zoom-leave-to {
  transform: scale(0.4);
}
</style>

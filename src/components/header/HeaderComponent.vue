<script lang="ts" setup>
import { onMounted, ref } from 'vue'

const header = ref();
const topHidden = ref(false);

const observer = new IntersectionObserver(
      (entries: IntersectionObserverEntry[]) => {
        entries.forEach((entry) => {
       
          topHidden.value = !entry.isIntersecting;    
          if(!entry.isIntersecting){
             //menu is gone go put a fixed value on it
             console.log('Fuck its gone');
   
          } else {
            console.log('There is is');
          }
           
        });
      },
      {
        threshold: 0.0,
      }
);

onMounted(()=> {
  observer.observe(header.value);
})
</script>

<template>
  <header ref="header">


    <!--<nav class="header navbar navbar-dark bg-dark flex-column">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">
          <img src="@/assets/logo.svg" alt=""  class="logo d-inline-block align-text-top">
        </a>
      </div>
    </nav>-->
  </header>


  
  
  <button v-if="topHidden" data-mdb-toggle="sidenav" data-mdb-target="#sidenav-1" class="btn btn-primary toggler" aria-controls="#sidenav-1" aria-haspopup="true">
    <i class="fas fa-bars"></i>
  </button>
</template>

<style scoped>
    @import "@/styles/header.scss";
</style>
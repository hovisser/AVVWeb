<script lang="ts" setup>
import { onMounted, ref } from 'vue';
import gsap from 'gsap';
import NavContactComponent from './NavContactComponent.vue';

const header = ref();
const showInfo = ref(false);
const menuShow = ref(false);
const showInfoAbout = ref(false);
const logoSmall = ref();


function onBeforeEnter(el: HTMLElement) {
  gsap.set(el, {
    scaleX: 0.25,
    scaleY: 0.25,
    opacity: 1
  })
}
  
function onEnter(el: HTMLElement, done: ()=>void) {
  showInfoAbout.value =false;
  const middle =(window.innerWidth/2);
  gsap.fromTo(el, {
    scale: 0.25,
    //duration: 0.5,
    x: -middle,
    y: -75,
  }, {
    scale: 1,
    //duration: 0.5,
    x: 0,
    y: 0,
    ease: 'bounce.out(2.5, 1)',
  });
}

function onLeave(el: HTMLElement, done: ()=>void) {
  //console.log('Go!!', logoSmall.value.offsetLeft);
  if(el) {
      const colWidth = (window.innerWidth/4);
      const imageWidth = 50;
      const offset = 45;
      const middle =(window.innerWidth/2);
      console.log('colwidth', colWidth, imageWidth, offset, middle);
      const loc =middle-offset;
      console.log('x is', loc);
   
      gsap.to(el, {
      
        duration: 0.7,
        scaleX: 0.25,
        scaleY: 0.25,
        x: -loc,
        y: -75,
        ease: 'bounce.out(2.5, 1)',
        
        onComplete: () => {
          console.log('leave', logoSmall.value);
          showInfoAbout.value = true;
          done();
        }
      });


   }
}

let timer:number|null = null;

const mouseEnter = () => {
  menuShow.value=true;
  if(timer) {
    clearTimeout(timer);
    timer = null;
  }
}

const mouseLeave = () => {
  timer = setTimeout(() => {
    menuShow.value=false;
  }, 3000);
}
</script>

<template>
  <header class="header" ref="header">
    <Transition @before-enter="onBeforeEnter"
                 @enter="onEnter"
                @leave="onLeave" appear>
           <svg class="logo_main d-block mx-auto mb-4" width="120" height="78" viewBox="0 0 120 78" fill="none" xmlns="http://www.w3.org/2000/svg"  
            @mouseenter="mouseEnter"
            @mouseleave="mouseLeave"
            @click="showInfo = !showInfo"
            v-if="!showInfo">
              <path d="M37.4999 1.50001C38.2519 0.500043 39.9999 0.500008 39.9999 0.500008H47.9999C47.9999 0.500008 49 0.5 51 1.50001C52.445 2.22251 53.5 5 53.5 5L77.5 51.5L103 5C103 5 104.5 2.5 106 1.5C107.5 0.5 109 0.5 109 0.5H117C117 0.5 118.841 0.499987 119.504 1.5C120.5 3.00002 118.998 5 118.998 5L79.9999 75.0118C79.9999 75.0118 78.9999 77.5 77.4999 77.5C75.9999 77.5 75.057 75.0118 75.057 75.0118L37.4936 6.00001C37.4936 6.00001 36.3719 3 37.4999 1.50001Z" fill="#545454"/>
              <path d="M54.5 76.5L53.5 52.5L76.5124 5C76.5124 5 77.8069 2.03279 79.5 0.999985C80.3198 0.499908 84 0.499908 84 0.499908H91C91 0.499908 93.5 0.500029 94 2.00002C94.5 3.5 93.4528 5 93.4528 5L54.5 76.5Z" fill="#545454"/>
              <path d="M14 60H50V47H14V60Z" fill="#545454"/>
              <path d="M2.5 2C3.94482 0.410695 7 0 7 0H24C24 0 26.3046 0.031229 28 1C29.8955 2.08312 31.5 5 31.5 5L60 66L55 75.5C55 75.5 54.5 77.5 53 77.5C51.5 77.5 50.5 75.5 50.5 75.5L19.5 14C19.5 14 18 11.5 16.5 11.5C15 11.5 15 14 15 14V74C15 74 14.9665 75.5335 14 76.5C13.0335 77.4665 11.5 77.5 11.5 77.5H4C4 77.5 2.4665 77.4665 1.5 76.5C0.533502 75.5335 0.5 74 0.5 74V6C0.5 6 1.18652 3.44482 2.5 2Z" fill="#545454"/>
              <path d="M18 47H15V44C15.5 46 16 46.5 18 47Z" fill="#545454"/>
              <path d="M34 47L36.5 47L35 44C36 46 35.5 46.5 34 47Z" fill="#545454"/>
              <path d="M18 60H15V63C15.5 61 16 60.5 18 60Z" fill="#545454"/>
              <path d="M40 60H43.5L44 62.5C43.5 61.5 42 60.5 40 60Z" fill="#545454"/>
              <path d="M79.5 48L77.5 51.5L75.5 48C76.6558 49.7336 78.3173 49.774 79.5 48Z" fill="#545454"/>
              <path d="M67 25L65.5 28.5L63.5 25C64.6558 26.7337 65.8174 26.774 67 25Z" fill="#545454"/>
              <path d="M55.5 49L53.5 52.5L51.75 49C52.9058 50.7336 54.3174 50.774 55.5 49Z" fill="#545454"/>
          </svg>
    </Transition>
    <Transition>
      <nav class="navbar navbar-expand-lg  navbar-dark bg-dark" v-if="showInfoAbout">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">
            <svg width="120" height="78" class="logo_small" ref="logoSmall" viewBox="0 0 120 78" fill="none" xmlns="http://www.w3.org/2000/svg"
              @mouseenter="mouseEnter"
              @mouseleave="mouseLeave"
              @click="showInfo = !showInfo">
              <path d="M37.4999 1.50001C38.2519 0.500043 39.9999 0.500008 39.9999 0.500008H47.9999C47.9999 0.500008 49 0.5 51 1.50001C52.445 2.22251 53.5 5 53.5 5L77.5 51.5L103 5C103 5 104.5 2.5 106 1.5C107.5 0.5 109 0.5 109 0.5H117C117 0.5 118.841 0.499987 119.504 1.5C120.5 3.00002 118.998 5 118.998 5L79.9999 75.0118C79.9999 75.0118 78.9999 77.5 77.4999 77.5C75.9999 77.5 75.057 75.0118 75.057 75.0118L37.4936 6.00001C37.4936 6.00001 36.3719 3 37.4999 1.50001Z" fill="#545454"/>
              <path d="M54.5 76.5L53.5 52.5L76.5124 5C76.5124 5 77.8069 2.03279 79.5 0.999985C80.3198 0.499908 84 0.499908 84 0.499908H91C91 0.499908 93.5 0.500029 94 2.00002C94.5 3.5 93.4528 5 93.4528 5L54.5 76.5Z" fill="#545454"/>
              <path d="M14 60H50V47H14V60Z" fill="#545454"/>
              <path d="M2.5 2C3.94482 0.410695 7 0 7 0H24C24 0 26.3046 0.031229 28 1C29.8955 2.08312 31.5 5 31.5 5L60 66L55 75.5C55 75.5 54.5 77.5 53 77.5C51.5 77.5 50.5 75.5 50.5 75.5L19.5 14C19.5 14 18 11.5 16.5 11.5C15 11.5 15 14 15 14V74C15 74 14.9665 75.5335 14 76.5C13.0335 77.4665 11.5 77.5 11.5 77.5H4C4 77.5 2.4665 77.4665 1.5 76.5C0.533502 75.5335 0.5 74 0.5 74V6C0.5 6 1.18652 3.44482 2.5 2Z" fill="#545454"/>
              <path d="M18 47H15V44C15.5 46 16 46.5 18 47Z" fill="#545454"/>
              <path d="M34 47L36.5 47L35 44C36 46 35.5 46.5 34 47Z" fill="#545454"/>
              <path d="M18 60H15V63C15.5 61 16 60.5 18 60Z" fill="#545454"/>
              <path d="M40 60H43.5L44 62.5C43.5 61.5 42 60.5 40 60Z" fill="#545454"/>
              <path d="M79.5 48L77.5 51.5L75.5 48C76.6558 49.7336 78.3173 49.774 79.5 48Z" fill="#545454"/>
              <path d="M67 25L65.5 28.5L63.5 25C64.6558 26.7337 65.8174 26.774 67 25Z" fill="#545454"/>
              <path d="M55.5 49L53.5 52.5L51.75 49C52.9058 50.7336 54.3174 50.774 55.5 49Z" fill="#545454"/>
            </svg>
          </a>

          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
              <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <div class="navbar-nav">
              <a class="nav-item nav-link active" href="#">Home <span class="sr-only">(current)</span></a>
              <a class="nav-item nav-link" href="#">Experience</a>
              <a class="nav-item nav-link" @click="showInfo = !showInfo" href="#">Contact</a>
            </div>
          </div>
        </div>
      </nav>
    </Transition>
    <Transition name="fade" @mouseenter="mouseEnter" @mouseleave="mouseLeave" >
      <NavContactComponent v-if="menuShow && !showInfoAbout" />
    </Transition>

  </header>


  

</template>

<style scoped>
    @import "@/styles/header.scss";
</style>
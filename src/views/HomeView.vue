<script setup lang="ts">

import { ref } from "vue";
import HeaderComponent from "../components/header/HeaderComponent.vue";

const showInfo = ref(true);
const showForm = ref(false);
const showLinkedin = ref(false);
const showTab = ref('none');
const showTopBar = ref(false);


</script>

<template>

  <div>
    <HeaderComponent />
    <main>
        <div class="px-4 py-5 my-5 text-center">

        
          <div class="info">
           
            <!--<div class="col-lg-6 mx-auto">
              <p class="lead mb-4">KYC Consultant</p>
         
              <div class="d-grid gap-2 d-sm-flex justify-content-sm-center">
                <Transition name="fade">
                  <div class="list-group list-group-horizontal"  v-if="showInfo" >
                    <a  @mouseover="showTab='mail'" class="list-group-item list-group-item-action"><i class="fa-solid fa-at"></i></a>
                    <a  @mouseover="showTab='whatsapp'"  class="list-group-item list-group-item-action"><i class="fa-brands fa-whatsapp"></i></a>
                    <a  @mouseover="showTab='slack'" class="list-group-item list-group-item-action"><i class="fa-brands fa-slack"></i></a>
                    <a  @mouseover="showTab='linked'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-linkedin"></i></a>
                    <a  @mouseover="showTab='insta'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-instagram"></i></a>
                    <a  @mouseover="showTab='facebook'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-facebook"></i></a>   
                  </div>
                </Transition>
              </div>     
            </div>-->
          </div>
          <!--<div class="content">
            <Transition name="slide-fade">
              <MailCompontent  v-if="showTab==='mail'"  @mouseleave="showTab='none';" />
            </Transition>
            <Transition name="slide-fade">
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='linked'" @mouseleave="showTab='none';">
                <div class="card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    linked in meuk
                  </div>
                </div>
              </div>
            </Transition>
            <Transition name="slide-fade">
              <WhatsappComponent :contact-number="31618663746" v-if="showTab==='whatsapp'"  />          
            </Transition>
            <Transition name="slide-fade">
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='discord'" @mouseleave="showTab='none';">
                <div class="card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    discord
                  </div>
                </div>
              </div>
            </Transition>
            <Transition name="slide-fade">
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='slack'" @mouseleave="showTab='none';">
                <div class="card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    slack
                  </div>
                </div>
              </div>
            </Transition>
            <Transition name="slide-fade">
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='insta'" @mouseleave="showTab='none';">
                <div class="card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    instagram
                  </div>
                </div>
              </div>
            </Transition>
         </div>-->
          
        <!--<div class="content">
          <AnimatedComponent id="el1" animation-type="fade">
            <div class="demo">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi eu
              enim feugiat, mollis risus eu, venenatis lorem. Nunc fermentum
              feugiat risus, at convallis turpis sollicitudin efficitur. Vivamus
              at fermentum lacus, blandit elementum ex. Sed pellentesque ornare
              sem, vel vehicula ligula consectetur id. Morbi quis justo ut lacus
              facilisis vulputate dignissim et orci. Fusce semper varius ante,
              quis dignissim erat sagittis vel. Sed in purus vitae ipsum efficitur
              faucibus. Aliquam eu sodales orci. Aenean id turpis porta, pretium
              arcu ut, pellentesque elit. Duis ultrices sapien eu laoreet tempus.
              Etiam condimentum lacus fringilla arcu tincidunt lobortis. Class
              aptent taciti sociosqu ad litora torquent per conubia nostra, per
              inceptos himenaeos. Etiam ex risus, venenatis accumsan orci sit
              amet, efficitur pretium risus. Vestibulum ante ipsum primis in
              faucibus orci luctus et ultrices posuere cubilia curae; Morbi nec
              odio neque. Phasellus in risus et quam efficitur tristique. Etiam
              tempus nisi in euismod pretium. Duis lacinia faucibus fermentum.
              Nunc tincidunt arcu eu urna pharetra tincidunt. Etiam dapibus ut
              nunc et congue. Integer eleifend accumsan urna, vel semper mi
              tincidunt non. Suspendisse et nulla a nunc sollicitudin
              sollicitudin. Duis in euismod leo. Nulla eleifend leo enim, in
              pellentesque tellus varius et. Etiam mattis nisi quis orci
              vulputate, varius porta mi vestibulum. Cras ultricies rutrum arcu,
              id sollicitudin est placerat id. Aliquam purus dui, lacinia a
              vehicula quis, consequat ut urna. Maecenas et felis felis. Phasellus
              laoreet posuere lorem et faucibus. Nam tristique leo vitae ligula
              laoreet gravida. Maecenas vitae metus nunc. Sed pellentesque et
              dolor faucibus vehicula. Integer non vehicula tellus. Vivamus justo
              sapien, porta quis erat eu, fringilla lacinia quam. Maecenas ut odio
              velit. Interdum et malesuada fames ac ante ipsum primis in faucibus.
              Vivamus a dui luctus, tincidunt diam a, varius quam. Praesent a
              suscipit arcu. Integer varius molestie leo, sed egestas turpis
              tincidunt eget. Cras elit lorem, posuere id velit id, convallis
              tincidunt tellus. Praesent eget risus pellentesque, sollicitudin est
              ut, fringilla felis. Ut congue justo eget ultricies iaculis. Ut vel
              metus at quam cursus bibendum. Duis congue ex et quam dignissim, nec
              hendrerit erat posuere. Vestibulum auctor odio vel fermentum cursus.
              Nunc convallis lobortis laoreet. Phasellus viverra, eros non sodales
              tempus, sem tortor elementum nisl, eget ultrices leo arcu eu elit.
              Nam pellentesque bibendum lectus mattis luctus. Integer feugiat
              mattis purus quis luctus. Morbi fringilla blandit lectus, ut egestas
              magna malesuada at. Fusce cursus a urna vel auctor. Fusce interdum
              nibh a neque blandit, eu fermentum dui vehicula. Quisque vel ipsum
              libero. Morbi vel nulla ultrices, pulvinar ligula egestas, gravida
              enim. Phasellus cursus dolor in consectetur rhoncus. In hac
              habitasse platea dictumst. Nam vulputate eros quis commodo laoreet.
              Integer hendrerit sollicitudin nunc vel tincidunt. Cras maximus nisi
              euismod eros consectetur imperdiet.
            </div>
          </AnimatedComponent>-->
   
   
      </div>
    </main>
  </div>
</template>

<style scoped>
    @import "@/styles/home.scss";
</style>

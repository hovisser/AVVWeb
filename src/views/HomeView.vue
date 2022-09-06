<script setup lang="ts">
import AnimatedComponent from "@/components/AnimatedComponent.vue";
import HeaderComponent from "@/components/header/HeaderComponent.vue";
import { ref } from "vue";

const showInfo = ref(false);
const showForm = ref(false);
const showLinkedin = ref(false);
const showTab = ref('none');
</script>

<template>
  <div class="px-4 py-5 my-5 text-center">
    <main>
    


        <div class="px-4 py-5 my-5 text-center">
          <AnimatedComponent id="el1" animation-type="fade">
            <img 
            class="logo_main d-block mx-auto mb-4"
            src="../assets/logo.svg"
            alt=""
            @mouseenter="showInfo=true; showTab='none';"
           />
          
          </AnimatedComponent>
        
          <div class="info">
           
            <div class="col-lg-6 mx-auto">
              <p class="lead mb-4">KYC Consultant</p>
         
              <div class="d-grid gap-2 d-sm-flex justify-content-sm-center">
                <Transition name="fade">
                  <div class="list-group list-group-horizontal"  v-if="showInfo" >
                    <a  @mouseover="showTab='mail'" class="list-group-item list-group-item-action"><i class="fa-solid fa-at"></i></a>
                    <a  @mouseover="showTab='linked'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-linkedin"></i></a>
                    <a  @mouseover="showTab='whatsapp'"  class="list-group-item list-group-item-action"><i class="fa-brands fa-whatsapp"></i></a>
                    <a  @mouseover="showTab='discord'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-discord"></i></a>
                    <a  @mouseover="showTab='slack'" class="list-group-item list-group-item-action"><i class="fa-brands fa-slack"></i></a>
                    <a  @mouseover="showTab='insta'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-instagram"></i></a>   
                   
                  </div>
                </Transition>
              </div> 
              
      
          
            </div>
            
          </div>
          <div class="content">
            <Transition name="slide-fade">
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='mail'" @mouseleave="showTab='none';">
                <div class="card email-card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    <h5 class="card-title">Laat een bericht achter:</h5>
                    <h6 class="card-subtitle mb-2 text-muted">Contact informatie:</h6>
                    <form>
                      <div class="form-group row">
                        <label for="colFormLabelSm" class="col-sm-2 col-form-label col-form-label-sm">Email</label>
                        <div class="col-sm-10">
                          <input type="email" class="form-control form-control-sm" id="colFormLabelSm" placeholder="email">
                        </div>
                      </div>
                    </form>
                    <span>
                      I will get in touch asap.
                    </span>
                  </div>
                </div>
              </div>    
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
              <div class="d-grid gap-4 d-sm-flex justify-content-sm-center" v-if="showTab==='whatsapp'" @mouseleave="showTab='none';">
                <div class="card" style="width: 20rem; margin-top: 5px;">
                  <div class="card-body">
                    <form>
                      <div class="form-group row">
                        <label for="colFormLabelSm" class="col-sm-2 col-form-label col-form-label-sm">Onderwerp</label>
                        <div class="col-sm-10">
                          <input type="text" class="form-control form-control-sm" id="colFormLabelSm" placeholder="Hallo ik wil graag contact opnemen">
                        </div>
                      </div>
                    </form>
                    <a class="btn btn-primary" href="https://wa.me/31618663746?text=I'm%20interested%20in%20your%20car%20for%20sale" >chat!</a>
                  </div>
                </div>
              </div>
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
         </div>
          
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
          </AnimatedComponent>
   
          <AnimatedComponent id="el2" animation-type="zoom">
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
          </AnimatedComponent>    
         </div>-->
   
      </div>
    </main>
  </div>
</template>

<style scoped>
    @import "@/styles/home.scss";
</style>

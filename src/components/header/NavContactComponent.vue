<script lang="ts" setup>

import { ref } from "vue";

import WhatsappComponent from "@/components/contact/WhatsappComponent.vue";
import MailCompontent from "@/components/contact/MailCompontent.vue";

const showTab = ref('none');
const showInfo = ref(false);

</script>

<template>
    <nav class="px-4 text-center">
        <div class="col-lg-6 mx-auto"> 
                <div class="d-grid gap-2 d-sm-flex justify-content-sm-center">
                    <div class="list-group list-group-horizontal"  >
                      <a  @mouseover="showTab='mail'" @click="showInfo = !showInfo" class="list-group-item list-group-item-action"><i class="fa-solid fa-at"></i></a>
                      <a  @mouseover="showTab='whatsapp'"  class="list-group-item list-group-item-action"><i class="fa-brands fa-whatsapp"></i></a>
                      <a  @mouseover="showTab='slack'" class="list-group-item list-group-item-action"><i class="fa-brands fa-slack"></i></a>
                      <a  @mouseover="showTab='linked'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-linkedin"></i></a>
                      <a  @mouseover="showTab='insta'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-instagram"></i></a>
                      <a  @mouseover="showTab='facebook'" href="#" class="list-group-item list-group-item-action"><i class="fa-brands fa-facebook"></i></a>   
                    </div>
                </div>     
        </div>
        <div class="content">
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
              <WhatsappComponent :contact-number="31618663746" v-if="showTab==='whatsapp'"  /> <!-- v-if="showTab==='whatsapp'"  -->              
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
    </nav>
</template>

<style lang="scss" scoped>

</style>
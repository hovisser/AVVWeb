<script lang="ts" setup>
import { onMounted, ref, defineProps } from "@vue/runtime-core";

const props = defineProps({
  businessName: {
    type: String,
    required: false,
    default: 'Avv Services'
  }, 
  businessUsername: {
    type: String,
    required: false,
    default: 'Amarins'
  },
  typeInMs: {
    type: Number,
    required: false,
    default: 1000
  }
});
   
const whatsApp = ref();
const typeing = ref(false);
const welcomeMessage =  ref('Hallo, wat leuk dat je met me in contact wil komen wat wil je weten?');
const whatsapp_state = ref('online');
const inputWhatsapp = ref();


const getTime = () => {
    const now = new Date();
    return `${now.getHours()}:${now.getMinutes()}`;
}

let timer: number|null = null;

const observer = new IntersectionObserver(
      (entries: IntersectionObserverEntry[]) => {
        entries.forEach((entry) => {
       
          //typeing.value = !entry.isIntersecting;   

          if(!entry.isIntersecting){
             //menu is gone go put a fixed value on i
             //typeing.value = false;
          } else {
            //typing animation
            console.log('Ther it is start');
            inputWhatsapp.value.focus();
            whatsapp_state.value = 'aan het typen...';
            if(timer) {
                clearTimeout(timer);
            } 

            timer = setTimeout(() => {

                    typeing.value = true;
                    console.log('done typing');
                    whatsapp_state.value = 'online'

            }, props.typeInMs);
          }
           
        });
      },
      {
        threshold: 0.0,
      }
);

onMounted(() => {
    observer.observe(whatsApp.value);
})

</script>

<template>
    <div class="whatsapp container" ref="whatsApp">
        <div class="row whatsapp_title">
            <div class="col-1">
            <img class="whatsapp_profile rounded-circle" src="../../assets/logo.svg" alt="{{ businessName }}" />
            </div>
            <div class="whatsapp_profile_info col-6 col-sm-auto">
                <h6 class="whatsapp_profile_name">{{ businessUsername }}</h6>
                <span class="whatsapp_profile_state">
                    {{ whatsapp_state }}
                </span>
            </div>
        </div>
        <div class="row whatsapp_content">
            <div class="col">
                        
                    <div class="whatsapp_bubble" v-if="typeing">
                        <div>
                            <p class="message">{{ welcomeMessage }}</p>
                            <div class="timestamp">{{ getTime() }}</div>
                        </div>
                    </div>
                
            </div>
            <div class="col">
            
            </div>
        </div>
        <div class="row whatsapp_form">
            <form>
            <div class="form-group row">
                <div class="col-2 col-sm-1">
                <img  class="whatsapp_icon" src="../../assets/smile.svg" alt="" />
                </div>
                <div class="col-8 col-sm-10">
                    <input ref="inputWhatsapp" type="text" class="form-control form-control-m whatsapp_input_text" id="colFormLabelSm" placeholder="Typ een bericht">
                </div>
                <div class="col-2 col-sm-1">
                <img  class="whatsapp_icon" src="../../assets/send.svg" alt="" />
                </div>
            </div>
            </form>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .whatsapp {
        margin-top: 5px;
        background-color: white;  
        border: 1px solid #F0F2F5;
        border-radius: 5px;
        -webkit-box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        -moz-box-shadow: rgba(0,0,0,0.3) 0 1px 3px;
        box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif !important;
        font-weight: 100;
        max-width: 50em;
        text-align: left;
    }
    
    .whatsapp_title {
        position: relative;
        height: 60px;
        background-color: #F0F2F5;
        text-align: center; 
        vertical-align: middle;
    }   
    .whatsapp_content {
        min-height: 10em;
        background-image: url('../../assets/wa_background.png');
        background-blend-mode: lighten;
    }
    .whatsapp_profile {
        margin-top: 10px;
        height: 40px;
        width: 40px;
        background-color: #fff;
    }
    .whatsapp_profile_name {
        margin-top: 20px;
        font-weight: 400;
    }
    
    .whatsapp_form {
        position: relative;
        height: 60px;
        background-color: #F0F2F5; 
    }
    
    .whatsapp_icon {
        cursor: pointer;
        margin-top: 20px;
    }
    
    .whatsapp_input_text {
        border: 0;
        box-shadow: none; /* You may want to include this as bootstrap applies these styles too */
        margin-top: 12px;    
    }
    
    .whatsapp_input_text::placeholder {
        color: #667781;
        opacity: 1;
    }
    
    .whatsapp_input_text::-ms-input-placeholder { /* Internet Explorer 10-11 */
        color: #667781;
    }
    
    .whatsapp_input_text::-ms-input-placeholder { /* Microsoft Edge */
        color: #667781;
    }

    .whatsapp_profile_state {
        position: absolute;
        font-size: 11px;
        bottom: 8px;
        color: #667781;
    }

    .whatsapp_profile_info {
        text-align: left;
    }

    .fade-enter-active,
    .fade-leave-active {
        transition: opacity 1s ease;
    }

    .fade-enter-from,
    .fade-leave-to {
        opacity: 0;
    }

    .whatsapp_bubble {
        margin-top: 8px;
        position: relative;
        background-color: white;  
        border: 1px solid #F0F2F5;
      
        border-radius: 0px 8px 8px;

      
        -webkit-box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        -moz-box-shadow: rgba(0,0,0,0.3) 0 1px 3px;
        box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        padding: 8px 8px 0px 10px;
        text-align: left;

        .message {
            font-size: 14px;
            font-weight: normal;
            margin-left: 0px;
            margin-bottom: 8px;
            color: #2b2b2b;
        }
        .timestamp{
            font-size: 11px;
            position: absolute;
            bottom: 1px;
            right: 10px;
            text-transform: uppercase; color: #999
        }

        ::after {
            position: absolute;
            right: 100%;
            top: 0%;
            content: "";
            height: 0;
            width: 0;
            border: 4px solid transparent;
            border-top-color: white;
            border-right-color: white;
            margin-top: 0px;
        }
    }
</style>
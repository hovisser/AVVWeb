<script lang="ts" setup>
import { faGaugeSimpleMed } from "@fortawesome/free-solid-svg-icons";
import { onMounted, ref, defineProps } from "@vue/runtime-core";
import sendIcon from '../../assets/vink.svg';
import recievedIcon from '../../assets/vink_send.svg';

enum ProfileState {
    Online = 'online',
    Typing = 'Aan het typen..',
    Offline= ''
}

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
  },
  contactNumber: { 
    type: Number,
    required: true
  },
  welcomeMessage: {
     type:String,
     required: false,
     default: 'Hallo wereld!'
  }
});

const whatsApp = ref();

const whatsappState = ref(ProfileState.Online);
const inputWhatsapp = ref();

const replyMessage = ref('');
const replyMessageStatusIcon = ref(sendIcon);

let timer: number|null = null;
let timerRead: number|null = null;

const zeroPad = (num: number, places: number) => {
  const zero = places - num.toString().length + 1;
  return Array(+(zero > 0 && zero)).join("0") + num;
}

const getTime = () => {
    const now = new Date();
    return `${now.getHours()}:${zeroPad(now.getMinutes(), 2)}`;
}

const addReply = () => {    
    if(inputWhatsapp.value instanceof HTMLInputElement) {        
        const replyInput: HTMLInputElement = inputWhatsapp.value;        
        replyMessage.value = replyInput.value;    
        //reset reply input
        replyInput.value = '';

        if(timerRead) {
            clearTimeout(timerRead);
        }

        timerRead = setTimeout(() => {
            replyMessageStatusIcon.value = recievedIcon;
            openWhatsapp(replyMessage.value);
        }, props.typeInMs);   
    }     
}

const openWhatsapp = (msg: string): boolean => {
    try {
        if(!msg) {
            return false;
        }

        const sendMessage = encodeURI(`https://wa.me/${props.contactNumber}?text=${msg}`);
        open(sendMessage, '_blank'); 
        return true;

    } catch(ex) {
        console.error(ex);
        return false;
    }    
}

const observer = new IntersectionObserver(
      (entries: IntersectionObserverEntry[]) => {
        entries.forEach((entry) => {                 
          if(entry.isIntersecting) {
                //typing animation            
                inputWhatsapp.value.focus();
                whatsappState.value = ProfileState.Typing;

                if(timer) {
                    clearTimeout(timer);
                } 

                timer = setTimeout(() => {                           
                    whatsappState.value = ProfileState.Online;
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
            <div class="col-2 col-sm-1">
            <img class="whatsapp_profile rounded-circle" src="../../assets/logo.svg" alt="{{ businessName }}" />
            </div>
            <div class="whatsapp_profile_info col-6 col-sm-auto">
                <h6 class="whatsapp_profile_name">{{ businessUsername }}</h6>
                <span class="whatsapp_profile_state">
                    {{ whatsappState }}
                </span>
            </div>
        </div>
        <div class="row whatsapp_content">
            <div class="row">
                <div class="col-10 col-sm-8">                        
                    <div class="whatsapp_bubble" v-if="whatsappState!==ProfileState.Typing">
                        <div>
                            <p class="message">{{ welcomeMessage }}</p>
                            <div class="timestamp">{{ getTime() }}</div>
                        </div>
                    </div>                
                </div>
                <div class="col col-sm float-end">
       
                </div>
            </div>
            <div class="row">
                <div class="col col-sm">                                                     
                </div>
                <div class="col-10 col-sm-8 float-end">
                    <div class="whatsapp_bubble alt" v-if="replyMessage">
                        <div>
                            <p class="message">{{ replyMessage }}</p>
                            
                            <div class="vink_send"><img  class="vink_icon" :src="replyMessageStatusIcon" alt="" /></div>
                            <div class="timestamp">{{ getTime() }}</div>
                        </div>
                    </div>       
                </div>
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
                <div class="col-2 col-sm-1" >
                    <img @click="addReply" class="whatsapp_icon" src="../../assets/send.svg" alt="" />
                </div>
            </div>
            </form>
        </div>
 
    </div>
</template>

<style lang="scss" scoped>

    $whatsapp_bg: #fff;
    $whatsapp_header: #f0f2f5;
    $whatsapp_bordercolor: $whatsapp_header;
    
    $whatsapp_bubble_bg: $whatsapp_header;
    $whatsapp_bubble_answer_bg: #d9fdd3;
    $whatsapp_bubble_answer_bordercolor: $whatsapp_bubble_answer_bg;

    $whatsapp_text: #000;
    $whatsapp_text_subcolor: #667781;

    .whatsapp {
        margin-top: 5px;
        position: relative;        
        background-color: $whatsapp_bg;  
        border: 1px solid $whatsapp_bordercolor;
        border-radius: 5px;
        -webkit-box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        -moz-box-shadow: rgba(0,0,0,0.3) 0 1px 3px;
        box-shadow: rgba(0, 0, 0, 0.3) 0px 1px 3px;
        font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif;
        font-weight: 100;
        color: $whatsapp_text;
        max-width: 40em;
        text-align: left;

        &_title {
            position: relative;
            height: 45px;
            background-color: $whatsapp_header;    
            vertical-align: middle;
        }   

        &_content {
            min-height: 10em;
            background-image: url('../../assets/wa_background.png');       
        }

        &_profile {
            margin-top: 5px;
            height: 35px;
            width: 35px;
            background-color:  $whatsapp_bg;

            &_name {
                margin-top: 10px;
                font-weight: 400;
            }

            &_state {
                position: absolute;
                font-size: 11px;
                bottom: 3px;
                color: $whatsapp_text_subcolor;
            }
        }

        &_form {
            position: relative;
            height: 45px;
            background-color: $whatsapp_header; 
        }

        &_icon {
            cursor: pointer;
            margin-top: 12px;
        }

        &_bubble {
            margin-top: 8px;
            position: relative;
            background-color: $whatsapp_bg;  
            border: 1px solid $whatsapp_bordercolor;      
            border-radius: 0px 8px 8px 8px;
            -webkit-box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
            -moz-box-shadow: rgba(0,0,0,0.3) 0 1px 3px;
            box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;        
            padding: 8px 8px 0px 10px;
            text-align: left;

            .timestamp {
                font-size: 11px;
                position: absolute;
                bottom: 1px;
                right: 10px;
                text-transform: uppercase; color: #999
            }

            .message {
                font-size: 14px;
                font-weight: normal;
                margin-left: 0px;
                margin-bottom: 8px;
           // color: #2b2b2b;
            }

            
            ::after {
                position: absolute;
                right: 100%;
                top: 0%;
                content: "";
                height: 0;
                width: 0;
                border: 4px solid transparent;
                border-top-color: $whatsapp_bg;
                border-right-color: $whatsapp_bg;
                margin-top: 0px;
            }

            &.alt {
                background-color: $whatsapp_bubble_answer_bg;
                border-radius: 8px 0px 8px 8px;

                .vink_send {
                    position: absolute;
                    bottom: 0px;
                    right: 45px;
                }

                ::before {
                    position: absolute;
                    left: 100%;
                    top: 0%;
                    content: "";
                    height: 0;
                    width: 0;
                    border: 4px solid transparent;
                    border-top-color: $whatsapp_bubble_answer_bordercolor;
                    border-left-color: $whatsapp_bubble_answer_bordercolor;
                    margin-top: 0px;
                }

                ::after {
                    display: none;
                }
            }
        }

        &_input_text {
            border: 0;
            box-shadow: none; /* You may want to include this as bootstrap applies these styles too */
            margin-top: 5px;    

            &::placeholder {
                color: $whatsapp_text_subcolor;
                opacity: 0.5;
            }

            &::-ms-input-placeholder { 
                color: $whatsapp_text_subcolor;
            }    
        }
    }
</style>
<script lang="ts" setup>
import { ref } from 'vue';


const mail = ref();
const isProfile = ref(true);

</script>

<template>

    <div class="mail container" ref="mail">
        <div class="row mail_title">
            <div class="col-2 col-sm-1">
            <!--<img class="mail_profile rounded-circle" src="../../assets/logo.svg" alt="{{ businessName }}" />-->
            </div>
            <div class="mail_profile_info col-6 col-sm-auto">
                <!--<h6 class="whatsapp_profile_name">{{ businessUsername }}</h6>
                <span class="whatsapp_profile_state">
                    {{ whatsappState }}
                </span>-->
            </div>
        </div>
        <form>
            <div class="row mail_content">
                <div class="row">
                    <div class="col form-group">
                        <label for="email">Email address</label>
                        <input type="email" class="form-control" id="email" name="email" aria-describedby="emailHelp" placeholder="Enter email">
                        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
                    </div>            
                </div>
                <div class="row">
                    <div class="form-group">
                        <label for="subject">Onderwerp</label>
                        <input type="text" class="form-control" id="subject" name="subject" placeholder="Subject*"/>
                    </div>
                </div>
                <div class="row">
                    <div class="form-group">
                        <label for="message">Bericht</label>
                        <textarea class="form-control" id="message" name="message" rows="3"></textarea>
                    </div>
                </div>
            </div>
            <div class="row mail_bottom">
                <button type="submit" class="btn btn-link" ><i class="fa-regular fa-paper-plane"></i></button>
            </div>
        </form>
    </div>
</template>

<style lang="scss" scoped>

    $mail_bg: #fff;
    $mail_header: #5E94D7;
    $mail_bordercolor: #5E94D7;
    .mail {
        margin-top: 5px;
        position: relative;        
        background-color: $mail_bg;  
        border: 1px solid $mail_bordercolor;
        border-radius: 5px;
        -webkit-box-shadow: rgba(0, 0, 0, 0.3) 0 1px 3px;
        -moz-box-shadow: rgba(0,0,0,0.3) 0 1px 3px;
        box-shadow: rgba(0, 0, 0, 0.3) 0px 1px 3px;
        font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif;
        font-weight: 100;
        max-width: 20em;
        text-align: left;

        &_title {
            position: relative;
            height: 45px;
            background-color: $mail_header;    
            vertical-align: middle;


        
        }   

        &_profile {
            position: relative;
            width: 50%;
            margin: 0 auto;

            vertical-align: middle;
        
        }

        &_content {
            min-height: 10em;
        }

        &_bottom {

            position: relative;
            height: 35px;
            background-color: $mail_header; 
            .btn {
                color: white;
                float: right;
            }
        }
    }
</style>
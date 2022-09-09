<script lang="ts" setup>
import { ref } from 'vue';


const mail = ref();

</script>

<template>
    <div class="mail container" ref="mail">
        <form>
        <div class="row">
            <div class="col">
                <input type="email" class="" placeholder="Email*"/>
            </div>            
        </div>
        <div class="row">
            <div class="col">
                <input type="text" class="" placeholder="Subject*"/>
            </div>
        </div>
        <div class="row">
            <div class="col">
                <textarea />
            </div>
        </div>
        <div class="row">
            <div class="col">
                <button type="submit" class="btn btn-submit" />
            </div>
        </div>
        </form>
    </div>
</template>

<style lang="scss" scoped>

    $mail_bg: #fff;
    $mail_header: #f0f2f5;
    $mail_bordercolor: #f0f2f5;
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
        max-width: 40em;
        text-align: left;
    }
</style>
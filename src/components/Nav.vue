<template>
<!--
header***
-->
    <header class="header" :class="login ? 'no_background' : 'black_background'">
<!--
shader***
-->
        <div class="shader" v-show="home" v-if="showVideo"></div>
        <nav class="header_nav flex flex_jc_sb flex_ai_c" :class="login ? 'big_nav' : 'small_nav'">
<!--
logo***
-->
            <a href="/" class="header_logo flex flex_ai_c">
                <img aria-label="Logo" src="@/assets/images/svg/logo.svg" loading="eager" alt="Logo">
            </a>
<!--
mobile menu icon***
-->
            <a href="#" ref="mobileToggle" @click="toggleOn" class="header_mobile_toggle">
                <span></span>
                <span></span>
                <span></span>
            </a>
<!--
nav links***
-->
            <div class="header_links">
                <router-link :class="login ? 'big_padding' : 'small_padding'" :to="{name:'Home'}">
                    Home
                </router-link>
                <div class="sub1">
                    <a class="sub_intel" :class="login ? 'big_padding' : 'small_padding'" href="#">Intel</a>
<!--
intel sub menu***
-->
                    <div class="intel_menu" :class="login ? 'top' : 'bottom'">
                        <a href="#">Foodie Intel</a>
                        <a href="#">Recommendations | Reviews</a>
                        <a href="https://thetravelintel.com/">Travel Intel</a>
                        <a href="https://destinationintel.com/">Destination Intel</a>
                        <a href="https://theentertainmentintel.com/">Entertainment &#38; Music Intel</a>
                        <a href="https://generousintel.com/">Generous Intel | Generous Empire</a>
                        <a href="https://cruiseintel.com/">Cruise Intel</a>
                        <a href="http://casinosintel.com/">Casinos Intel</a>
                        <a href="https://worldsintel.com/">World's Intel | Business | Lifestyle | VIP</a>
                        <a href="https://worldsintel.com/">World's Business Intel</a>
                    </div>
                </div>
                <div class="sub2">
                    <a class="sub_benefits" :class="login ? 'big_padding' : 'small_padding'" href="#">Benefits</a>
<!--
benefits sub menu***
-->
                    <div class="benefits_menu" :class="login ? 'top' : 'bottom'">
                        <router-link :to="{name:'Destinations'}">Complimentary Vacation Destinations</router-link>
                        <a href="https://redeemvacations.com/">Manage Your Complimentary Vacation</a>
                        <a href="https://redeemvacations.com/terms-and-conditions">Complimentary Vacation Terms &#38; Conditions</a>
                        <a href="https://www.diningadvantage.com/">Dining Club | Dining Advantage Offers</a>
                    </div>
                </div>
                <div class="sub3">
                    <a class="sub_more" :class="login ? 'big_padding' : 'small_padding'" href="#">More</a>
<!--
more sub menu***
-->
                    <div class="more_menu" :class="login ? 'top' : 'bottom'">
                        <a href="#">Member Plans &#38; Pricing</a>
                        <a href="#">Member Profiles</a>
                        <a href="https://issuu.com/thevipmedia/docs/travel_intel_1">Travel Intel Magazine</a>
                        <a href="https://issuu.com/thevipmedia/docs/suncoast_magazine_fall.19">Suncoast Magazine</a>
                        <a href="#">Stories</a>
                        <a href="https://worldstravelagency.com/">World's Travel Agency</a>
                        <a href="#">Offers</a>
                        <a href="#">Giveaways</a>
                        <a href="#">Events</a>
                        <a href="#">Event Calendar</a>
                        <a href="https://founderscard.com/inquire?code=FCTRACY413">Founders Card Membership</a>
                        <a href="https://issuu.com/signin?onLogin=%2Fhome%2Fpublished%2Fprintable_certificates">Generous Vacations Printable Certificates</a>
                        <a href="https://foodieintel.com/images/Foodie-Intel-Media-Kit.pdf">Foodie Intel Media Kit</a>
                        <a href="https://issuu.com/thevipmedia/docs/foodie_intel_media_kit_40988768746d08">Foodie Intel Media Kit Magazine</a>
                        <a href="#">Videos</a>
                        <a href="#">Photos</a>
                        <a href="#">Audio</a>
                    </div>
                </div>
                <a href="#" :class="login ? 'big_padding' : 'small_padding'">Rewards</a>
                <router-link :class="login ? 'big_padding' : 'small_padding'" :to="{name:'Contact'}">
                    Contact
                </router-link>
                <router-link :class="login ? 'big_padding' : 'small_padding'" :to="{name:'Login'}">
                    Login
                </router-link>
            </div>
        </nav>
    </header>
<!--
mobile menu***
-->
    <div class="header_mobile_menu flex flex_dr_c flex_ai_c flex_jc_c" v-if="toggled_mobile_menu">
        <div class="container">
            <router-link :to="{name:'Home'}">
                Home
            </router-link>
            <a @click="intel" href="#">Intel</a>
<!--
intel mobile sub menu***
-->
            <div class="mobile_menu flex flex_dr_c flex_ai_c flex_jc_c" v-if="sub_intel">
                <div class="container">
                    <a @click="exit" href="#"><i class="fas fa-caret-left"></i> Back</a>
                    <a href="#">Foodie Intel</a>
                    <a href="#">Recommendations | Reviews</a>
                    <a href="https://thetravelintel.com/">Travel Intel</a>
                    <a href="https://destinationintel.com/">Destination Intel</a>
                    <a href="https://theentertainmentintel.com/">Entertainment &#38; Music Intel</a>
                    <a href="https://generousintel.com/">Generous Intel | Generous Empire</a>
                    <a href="https://cruiseintel.com/">Cruise Intel</a>
                    <a href="http://casinosintel.com/">Casinos Intel</a>
                    <a href="https://worldsintel.com/">World's Intel | Business | Lifestyle | VIP</a>
                    <a href="https://worldsintel.com/">World's Business Intel</a>
                </div>
            </div>
            <a @click="benefits" href="#">Benefits</a>
<!--
benefits mobile sub menu***
-->
            <div class="mobile_menu flex flex_dr_c flex_ai_c flex_jc_c" v-if="sub_benefits">
                <div class="container">
                    <a @click="exit" href="#"><i class="fas fa-caret-left"></i> Back</a>
                    <router-link :to="{name:'Destinations'}">Complimentary Vacation Destinations</router-link>
                    <a href="https://redeemvacations.com/">Manage Your Complimentary Vacation</a>
                    <a href="https://redeemvacations.com/terms-and-conditions">Complimentary Vacation Terms &#38; Conditions</a>
                    <a href="https://www.diningadvantage.com/">Dining Club | Dining Advantage Offers</a>
                </div>
            </div>
            <a @click="more" href="#">More</a>
<!--
more mobile sub menu***
-->
            <div class="mobile_menu flex flex_dr_c flex_ai_c flex_jc_c" v-if="sub_more">
                <div class="container">
                    <a @click="exit" href="#"><i class="fas fa-caret-left"></i> Back</a>
                    <a href="#">Member Plans &#38; Pricing</a>
                    <a href="#">Member Profiles</a>
                    <a href="https://issuu.com/thevipmedia/docs/travel_intel_1">Travel Intel Magazine</a>
                    <a href="https://issuu.com/thevipmedia/docs/suncoast_magazine_fall.19">Suncoast Magazine</a>
                    <a href="#">Stories</a>
                    <a href="https://worldstravelagency.com/">World's Travel Agency</a>
                    <a href="#">Offers</a>
                    <a href="#">Giveaways</a>
                    <a href="#">Events</a>
                    <a href="#">Event Calendar</a>
                    <a href="https://founderscard.com/inquire?code=FCTRACY413">Founders Card Membership</a>
                    <a href="https://issuu.com/signin?onLogin=%2Fhome%2Fpublished%2Fprintable_certificates">Generous Vacations Printable Certificates</a>
                    <a href="https://foodieintel.com/images/Foodie-Intel-Media-Kit.pdf">Foodie Intel Media Kit</a>
                    <a href="https://issuu.com/thevipmedia/docs/foodie_intel_media_kit_40988768746d08">Foodie Intel Media Kit Magazine</a>
                    <a href="#">Videos</a>
                    <a href="#">Photos</a>
                    <a href="#">Audio</a>
                </div>
            </div>
            <a href="#">Rewards</a>
            <router-link :to="{name:'Contact'}">
                Contact
            </router-link>
            <router-link :to="{name:'Login'}">
                Login
            </router-link>
            <a @click="close" href="#"><i class="fas fa-times"></i> Exit</a>
        </div>
    </div>
</template>

<script>
    import { ref } from 'vue'

    export default {
        props: ['login','home','showVideo'],
        setup(props,context){
            
            const toggled_mobile_menu = ref(false)
            const mobileToggle = ref(null)
            const sub_intel = ref(false)
            const sub_benefits = ref(false)
            const sub_more = ref(false)
            
            const toggleOn = ()=>{
                if(!mobileToggle.value.classList.contains('header_open')){
                    mobileToggle.value.classList.add('header_open')
                    toggled_mobile_menu.value = true
                }
            }

            const intel = ()=>{
                sub_intel.value = true
            }

            const benefits = ()=>{
                sub_benefits.value = true
            }

            const more = ()=>{
                sub_more.value = true
            }

            const exit = ()=>{
                sub_intel.value = false
                sub_benefits.value = false
                sub_more.value = false
            }

            const close = ()=>{
                toggled_mobile_menu.value = false
                mobileToggle.value.classList.remove('header_open')
            }

            return{toggleOn,mobileToggle,intel,sub_intel,exit,sub_benefits,benefits,more,sub_more,close,toggled_mobile_menu}
        }
    }
</script>
<script>

import Swiper from 'swiper';
import SliderCard from './common/SliderCard.vue';
import dataSlider from './common/mock/slider.json'

export default {
    data() {
        return {
           
            activeIndex: 1,
            slider: null,
            loop: true,
            dataSlider
        };
    },
    mounted() {
        this.initSwiper();
    },
    methods: {
        initSwiper() {
            this.slider = new Swiper(this.$refs.swiperEl, {
                slidesPerView: 3,
                spaceBetween: 25,
                centeredSlides: true,
                initialSlide: 1,
            });
            this.slider?.on('slideChange', swiper => {
                this.activeIndex = swiper.activeIndex;
            });
        },
        clickNextSlide() {
            this.slider.slideNext();
        },
        clickPrevSlide() {
            this.slider.slidePrev();
        }
    },
    computed: {
        isEnd() {
            return this.activeIndex === dataSlider.length - 1;
        },
        isStart() {
            return this.activeIndex === 0;
        }
    },
    components: { SliderCard }
}
</script>
<template>
    <div class="bg-image">
        <div class="title">
            <div class="title__text">
                <p>Становитесь своим собственным банком</p>
                <p>Получите свободу, благодаря конфиденциальным, глобальным цифровым деньгам. Становитесь своим собственным банком с полным контролем над своими цифровыми активами.</p>
            </div>
            <img src="../assets/images/coin.png" alt="coins">
        </div>
    <div class="container">
      <div ref="swiperEl" class="swiper">
          <div class="swiper-wrapper">
              <SliderCard
                  :key="key"
                  v-for="(card,key) in dataSlider"
                  :card="card"
                  class="swiper-slide"
                  :active="this.activeIndex === key"
              />
          </div>
      </div>
    </div>
    <div class="navigation">
        <button  :class="{'disabled': isStart}" @click="clickPrevSlide"> 
          prev
        </button>
        <button :class="{'disabled': isEnd}" @click="clickNextSlide">
          nex
        </button>
    </div>
</div>

</template>
<style lang="scss" scoped>



.title{
    
   
    display: flex;
    justify-content: center;
    padding-top: 200px;

    
    
    &__text{
        width: 69.8rem;
        height: 23.4rem;
        gap: 16px;
        opacity: 0px;
    }
    &__text :nth-child(1){
        font-size: 5.6rem;
        font-weight: bold;
        font-weight: 800;
        line-height: 61px;
        text-align: left;
        background: linear-gradient(91.92deg, #FFFFFF 29.24%, rgba(176, 250, 255, 0) 131.64%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin: 0;


    }
    &__text :nth-child(2){
        font-size: 1.8rem;
        font-weight: 600;
        line-height: 32px;
        text-align: left;
        color: white;

        
    }

}


.swiper{
    width: 100%;
    overflow: hidden;
}
.navigation{
    display: flex;
    justify-content: center;
    gap: 10px;
    align-items: center;
    width: 100vw;
    padding: 0 20px;
    .navigation button {
          display: flex;
          justify-content: center;
          align-items: center;
          outline: none;
          background-color: transparent;
          color: white;
          font-size: 40px;
          cursor: pointer;
          border: 1px solid white;
          border-radius: 50%;
          width: 60px;
          height: 60px;
          
      }
}
.navigation button.disabled{
    cursor: not-allowed;
    opacity: .5;
    transition: all .3s ease-in-out;
}


</style>
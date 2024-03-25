<template>
    <div :class="['SlideCard',$style.SlideCard,{[$style['_active']]:active}]" >
        <span>{{ card.subtitle }}</span>
        <span>{{ card.title }}</span>
        <span>{{ card.text }}</span>
        <button class="SlideCard__btn">Перейти и получить</button>
    </div>

</template>
<script>
export default{
    name:'SliderCard',
    props:{
        card:{
            type: Object,
            required:true,
        },
        active:{
            type: Boolean,
            default: false,
            required: false
        }
    }
}
</script>
<style lang="scss" module>

.SlideCard{
    display: flex;
    flex-direction: column;
    width: calc(33% - 25px);
    height: 46rem;
    background-color: rgba(21, 24, 34, 1);
    opacity: .5;
    transition: all .3s ease-in-out;
    cursor: pointer;
    padding: 3rem;
    &:global(.swiper-slide){
        transform: translateY(100px);
    }
    
    
}
.SlideCard._active{
    opacity: 1;
    transform: translateY(0);
}

.SlideCard :nth-child(1){
    font-size: 1.8rem;
    color: white;
    
}
.SlideCard :nth-child(2){
    color: white;
    font-size: 3.2rem;
    font-weight: bold;
    
}
.SlideCard :nth-child(3){
    color: white;
    font-size: 1.6rem;
    margin-top: 2rem;
    margin-bottom: 2rem;
}

.SlideCard__btn{
        width: 22.4rem;
        height: 5.4rem;
        color: aqua;
    }

</style>
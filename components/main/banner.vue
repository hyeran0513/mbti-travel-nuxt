<template>
  <section>
    <div class="swiper-area">
      <swiper
        :slidesPerView="1"
        :spaceBetween="30"
        :navigation="{ nextEl: '.swiper-banner-next', prevEl: '.swiper-banner-prev' }"
        :pagination="{
          type: 'fraction'
        }"
        :autoplay="{ delay: 2500, disableOnInteraction: false }"
        :modules="[Navigation, Pagination, Autoplay]">
        <swiper-slide v-for="i in 5" :key="i" class="companion">
          <div class="item">
            <img :src="sampleImg01" />
          </div>
        </swiper-slide>

        <button type="button" class="swiper-button swiper-banner-prev swiper-button-prev"></button>
        <button type="button" class="swiper-button swiper-banner-next swiper-button-next"></button>
      </swiper>
    </div>
  </section>
</template>

<script setup>
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import sampleImg01 from '@/assets/images/sample/sample01.jpg';
</script>

<style lang="scss" scoped>
section {
  margin-bottom: 60px;

  .swiper-area {
    margin: 0 auto;
    max-width: 1920px;

    .swiper {
      .item {
        height: 500px;
      }
    }
  }
}
</style>

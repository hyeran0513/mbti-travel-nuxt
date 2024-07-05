<template>
   <section>
      <div class="section-title">여행지 찾기</div>

      <div class="swiper-area">
        <swiper
          :slidesPerView="4"
          :spaceBetween="30"
          :navigation="{ nextEl: '.swiper-destination-next', prevEl: '.swiper-destination-prev' }"
          :modules="[Navigation]">
          <swiper-slide v-for="i in 5" :key="i" class="companion">
            <div class="item">
              <NuxtLink to="/">
                <div class="thumb">
                  <div class="thumb-img"></div>
                </div>

                <div class="info">
                  <div class="info-title">제목</div>
                  
                  <div class="info-location">
                    <i class="icon-fill-pin" />
                    <span class="txt">위치</span>
                  </div>
                </div>
              </NuxtLink>
            </div>
          </swiper-slide>
        </swiper>

        <button type="button" class="swiper-button swiper-destination-prev swiper-button-prev"></button>
        <button type="button" class="swiper-button swiper-destination-next swiper-button-next"></button>
      </div>
    </section>
</template>


<script setup>
import { Navigation } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
</script>

<style lang="scss" scoped>
  section {
    .section-title {
      margin-bottom: 20px;
      font-size: 18px;
      font-weight: bold;
    }

    .swiper-area {
      position: relative;
      margin: 0 -20px;
      padding: 0 20px;
      max-width: 1240px;
      
      .swiper {
        .item {
          border-radius: 12px;
          overflow: hidden;

          &:hover {
            .info {
              &-title {
                text-decoration: underline;
              }
            }
          }

          .thumb {
            width: 100%;
            height: 200px;

            &-img {
              width: 100%;
              height: 100%;
              background: #d7d7d7;
            }
          }

          .info {
            position: absolute;
            bottom: 20px;
            left: 20px;

            &-title {
              font-size: 18px;
              font-weight: bold;
              transition: all ease .3s;
            }

            &-location {
              & > i {
                margin-right: 4px;
              }
            }
          }
        }

        &-button {
          position: absolute;
          top: 50%;
          width: 40px;
          height: 40px;
          border-radius: 50%;
        }
      }

      .swiper-button-prev {
        left: 0;
        color: #333;
        background: #FFF;
        box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.24);

        &:after {
          content: "\e936";
          font-family: 'iconFont';
          font-size: 24px;
        }
      }

      .swiper-button-next {
        right: 0;
        color: #333;
        background: #FFF;
        box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.24);

        &:after {
          content: "\e937";
          font-family: 'iconFont';
          font-size: 24px;
        }
      }
    }
  }
</style>
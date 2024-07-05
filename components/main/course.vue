<template>
   <section>
      <div class="section-title">여행코스</div>

      <div class="swiper-area">
        <swiper
          :slidesPerView="3"
          :spaceBetween="30"
          :navigation="{ nextEl: '.swiper-course-next', prevEl: '.swiper-course-prev' }"
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

                  <div class="info-period">1박 2일</div>
                </div>
              </NuxtLink>
            </div>
          </swiper-slide>
        </swiper>

        <button type="button" class="swiper-button swiper-course-prev swiper-button-prev"></button>
        <button type="button" class="swiper-button swiper-course-next swiper-button-next"></button>
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
          position: relative;
          border-radius: 12px;
          border-left: 1px solid #d7d7d7;
          border-right: 1px solid #d7d7d7;
          border-bottom: 1px solid #d7d7d7;
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
            padding: 20px 30px;

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

            &-period {
              position: absolute;
              top: 150px;
              right: 20px;
              display: inline-block;
              padding: 4px 14px;
              color: #FFF;
              background: var(--primary-color);
              border-radius: 4px 14px;
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
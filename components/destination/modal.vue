<template>
  <div class="modal" v-if="modalShow">
    <div class="modal-container">
      <div class="modal-head">
        <p class="title">여행지명</p>
        <button type="button" class="btn-close" @click="modalClose"><i class="icon-x" /></button>
      </div>

      <div class="modal-body">    
        <div class="swiper-area">
          <swiper
            :style="{
              '--swiper-navigation-color': '#fff',
              '--swiper-pagination-color': '#fff',
            }"
            :spaceBetween="10"
            :navigation="true"
            :thumbs="{ swiper: thumbsSwiper }"
            :modules="modules"
            class="mySwiper2"
            ref="mainSwiper"
            v-if="initialized"
          >
            <swiper-slide v-for="(image, index) in images" :key="'main-' + index">
              <img :src="image" />
            </swiper-slide>
          </swiper>
          <swiper
            @swiper="setThumbsSwiper"
            :loop="true"
            :spaceBetween="10"
            :slidesPerView="10"
            :freeMode="true"
            :watchSlidesProgress="true"
            :modules="modules"
            class="mySwiper"
            ref="thumbSwiper"
            v-if="initialized"
          >
            <swiper-slide v-for="(image, index) in images" :key="'thumb-' + index">
              <img :src="image" />
            </swiper-slide>
          </swiper>
        </div>
      </div>

      <div class="modal-footer">
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, nextTick, onUnmounted } from "vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css/free-mode';
import 'swiper/css/navigation';
import 'swiper/css/thumbs';
import { FreeMode, Navigation, Thumbs } from 'swiper/modules';

const modalShow = ref(false);
const initialized = ref(false);
const thumbsSwiper = ref(null);
const mainSwiper = ref(null);
const thumbSwiper = ref(null);

const modalOpen = () => {
  initialized.value = false;
  modalShow.value = true;
  nextTick(() => {
    initialized.value = true;
  });
}

const modalClose = () => {
  destroySwipers();
  modalShow.value = false;
}

const destroySwipers = () => {
  if (mainSwiper.value?.swiper) {
    mainSwiper.value.swiper.destroy(true, true);
  }
  if (thumbSwiper.value?.swiper) {
    thumbSwiper.value.swiper.destroy(true, true);
  }
  thumbsSwiper.value = null;
}

const setThumbsSwiper = (swiper) => {
  thumbsSwiper.value = swiper;
};

const images = [
  'https://swiperjs.com/demos/images/nature-2.jpg',
  'https://swiperjs.com/demos/images/nature-3.jpg',
  'https://swiperjs.com/demos/images/nature-4.jpg',
  'https://swiperjs.com/demos/images/nature-5.jpg',
  'https://swiperjs.com/demos/images/nature-6.jpg',
  'https://swiperjs.com/demos/images/nature-7.jpg',
  'https://swiperjs.com/demos/images/nature-9.jpg',
  'https://swiperjs.com/demos/images/nature-10.jpg',
  'https://swiperjs.com/demos/images/nature-9.jpg',
  'https://swiperjs.com/demos/images/nature-10.jpg',
];

const modules = [FreeMode, Navigation, Thumbs];

watch(modalShow, (newVal) => {
  document.querySelector('body').style.overflow = newVal ? 'hidden' : '';
  if (!newVal) {
    destroySwipers();
  }
});

defineExpose({
  modalOpen,
  modalClose,
});

onUnmounted(() => {
  destroySwipers();
});
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,.4);
  z-index: 1000;

  &-container {
    display: flex;
    flex-direction: column;
    width: 1200px;
    max-width: 100%;
    box-shadow: 1px 0 10px rgba(0,0,0,.2);
    background: #FFF;
    border-radius: 20px;
    overflow: hidden;
  }

  &-head {
    display: flex;
    align-items: flex-start;
    padding: 40px 40px 30px;
    border-radius: 20px 20px 0 0;

    .title {
      flex: 1;
      font-size: 24px;
      font-weight: bold;
    }

    .btn-close {
      font-size: 20px;
    }
  }

  &-body {
    flex: 1;
    padding: 0 40px;
    line-height: 1.4;
    margin: -0.14em 0;
    max-height: 90%;
    overflow: hidden;
    overflow-y: auto;
  }

  &-footer {
    display: flex;
    padding-top: 40px;

    &::v-deep([class^=btn]) {
      flex: 1;
      border-radius: 0;
      margin: 0;
      height: 50px;
      line-height: 50px;

      &[class*=gray] {
        color: #999;
      }

      &[class*=main] {
        background: var(--primary-color);
        color: #FFF;
      }
    }
  }
}

.swiper-area {
        margin: 0 auto;
        max-width: 1920px;
        height: 500px;
      }

      .swiper {
        width: 100%;
        height: 100%;
      }

      .swiper-slide {
        text-align: center;
        font-size: 18px;
        background: #fff;

        display: flex;
        justify-content: center;
        align-items: center;
      }

      .swiper-slide img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

      .swiper {
        width: 100%;
        height: 300px;
        margin-left: auto;
        margin-right: auto;
      }

      .swiper-slide {
        background-size: cover;
        background-position: center;
      }

      .mySwiper2 {
        height: 80%;
        width: 100%;
      }

      .mySwiper {
        margin-top: 20px;
        height: 20%;
        box-sizing: border-box;
        padding: 10px 0;
        

        .swiper-slide {
          img {
            border-radius: 12px;
          }
        }
      }

      .mySwiper .swiper-slide {
        width: 25%;
        height: 100%;
        opacity: 0.4;
      }

      .mySwiper .swiper-slide-thumb-active {
        opacity: 1;
      }

      .swiper-slide img {
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
      }

</style>
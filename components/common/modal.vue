<template>
  <div class="modal" v-if="modalShow">
    <div class="modal-container">
      <div class="modal-head">
        <p class="title"><slot name="title" /></p>
        <button type="button" class="btn-close" @click="modalClose"><i class="icon-x" /></button>
      </div>

      <div class="modal-body">
        <slot />
      </div>

      <div class="modal-footer">
        <slot name="footer" />
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from "vue";
const modalShow = ref(false);

const modalOpen = () => {
  modalShow.value = true;
}

const modalClose = () => {
  modalShow.value = false;
}

watch(() => modalShow.value, () => {
  document.querySelector('body').style.overflow = modalShow.value ? 'hidden' : '';
});

defineExpose({
  modalOpen,
  modalClose,
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
    width: 500px;
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
    max-height: 50vh;
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
</style>
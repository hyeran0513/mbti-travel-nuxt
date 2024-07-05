<template>
  <div class="header">
    <div class="header-inner">
      <ul class="gnb">
        <li class="gnb-item" v-for="(gnbItem, gnbIdx) in gnb" :key="gnbIdx">
          <NuxtLink :to="gnbItem?.LINK">{{ gnbItem?.TEXT }}</NuxtLink>
        </li>
      </ul>

      <NuxtLink to="/" class="logo">로고</NuxtLink>

      <div class="btn-wrap">
        <NuxtLink to="/" class="btn-mypage">
          <i class="icon-user" />
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
  const gnb = ref([
    {
      TEXT: '여행지 찾기',
      LINK: '/'
    },
    {
      TEXT: '동행자 찾기',
      LINK: '/'
    },
    {
      TEXT: '여행코스',
      LINK: '/'
    }
  ]);
</script>

<style lang="scss" scoped>
.header {
  height: 80px;

  &-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    max-width: 1200px;
    height: 100%;

    .gnb {
      display: flex;
      align-items: center;
      gap: 30px;
      height: 100%;
      transition: all ease .3s;
      flex: 1;

      &-item {
        & > a {
          &:hover {
            color: var(--primary-color);
          }
        }
      }
    }

    .logo {
      flex: 1;
    }

    .btn-wrap {
      display: flex;

      .btn-mypage {
        width: 40px;
        height: 40px;
        line-height: 38px;
        text-align: center;
        border: 1px solid #d7d7d7;
        border-radius: 4px;
      }
    }
  }
}
</style>
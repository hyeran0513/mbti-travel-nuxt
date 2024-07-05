<template>
  <div>
    <!-- 배너 -->
    <mainBanner />

    <div class="section-area">
      <!-- 여행지 찾기 -->
      <mainDestination />

      <!-- 여행코스 -->
      <mainCourse />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.section-area {
  display: flex;
  flex-direction: column;
  gap: 50px;
  margin: 0 auto;
  max-width: 1200px;
}
</style>
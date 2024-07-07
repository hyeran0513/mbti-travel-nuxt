<template>
  <div class="section-area">
    <section class="section-thumb">
      <div class="img-wrap">
        <div class="img1">
          <div class="item"></div>
        </div>

        <div class="img2">
          <div class="item"></div>
        </div>

        <div class="img3">
          <div class="item"></div>
        </div>

        <div class="img4">
          <div class="item"></div>
        </div>

        <div class="img5">
          <div class="item"></div>
        </div>
      </div>

      <button type="button" class="btn-all-img" @click="modal.modalOpen()">사진 모두 보기</button>
    </section>

    <section class="section-title">
      <div class="title">여행지명</div>

      <div class="count">
        <dl class="count-item comment">
          <dt>댓글</dt>
          <dd>10</dd>
        </dl>

        <dl class="count-item view">
          <dt>조회수</dt>
          <dd>10</dd>
        </dl>

        <dl class="count-item like">
          <dt>좋아요</dt>
          <dd>10</dd>
        </dl>
      </div>
    </section>

    <section class="section-detail">
      <p class="title">상세정보</p>

      <div class="cont">상세</div>
    </section>

    <section class="section-comment">
      <p class="title">댓글</p>

      <div class="cont">
        <CommonCommentForm />
        <CommonCommentList />
      </div>
    </section>
  </div>

  <DestinationModal ref="modal" />
</template>

<script setup>
const modal = ref();
</script>

<style lang="scss" scoped>
  .section-area {
    .section {
      &-thumb {
        position: relative;
        margin: 0 auto;
        max-width: 1200px;

        .img-wrap {
          max-width: 1200px;
          display: grid;
          grid-auto-flow: column;
          gap: 8px;

          .img1 {
            grid-row: span 2 / span 2;
            position: relative;

            .item {
              height: 512px;
              width: 640px;
              background: #f8f8f8;
              border-radius: 12px;
            }
          }

          .img2, .img3, .img4, .img5 {
            grid-column: span 1 / span 1;
            position: relative;

            .item {
              height: 252px;
              width: 272px;
              background: #f8f8f8;
              border-radius: 12px;
            }
          }
        }

        .btn-all-img {
          position: absolute;
          bottom: 30px;
          right: 30px;

          display: flex;
    -webkit-box-align: center;
    align-items: center;
    justify-content: center;
    height: 40px;
    min-width: 40px;
    border-radius: 400px;
    font-size: 0.875rem;
    line-height: normal;
    letter-spacing: 0px;
    font-weight: 600;
    box-shadow: 0 2px 8px rgba(0,0,0,0.24);
    cursor: pointer;
    padding: 12px 16px 12px 14px;
    background-color: rgb(255, 255, 255);
        }
      }
      
      &-title {
        margin: 50px auto 0;
        max-width: 1200px;

        .title {
          font-size: 2rem;
          font-weight: bold;
        }

        .count {
          display: flex;
          gap: 10px;

          &-item {
            display: flex;
            font-size: 1rem;
          }
        }
      }

      &-detail {
        margin: 50px auto 0;
        max-width: 1200px;

        & > .title {
          margin-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
        }
      }

      &-comment {
        margin: 50px auto 0;
        max-width: 1200px;

        & > .title {
          margin-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
        }
      }
    }
  }
</style>

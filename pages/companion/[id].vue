<template>
  <div class="section-area">
    <section class="section-thumb">
      <div class="thumb">
        <div class="thumb-img"></div>
      </div>
    </section>

    <section class="section-title">
      <div class="title">경주 여행 같이 가실 분 모집합니다</div>

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

    <section class="section-schedule">
      <p class="title">여행일정</p>

      <div class="cont">
        <div class="info">
          <dl class="info-item">
            <dt>
              <i class="icon-calendar" />
              <span class="txt">여행일정</span>
            </dt>

            <dd>2024.07.07 ~ 2024.07.08</dd>
          </dl>

          <dl class="info-item">
            <dt>
              <i class="icon-outline-pin" />
              <span class="txt">위치</span>
            </dt>

            <dd>강릉</dd>
          </dl>

          <dl class="info-item">
            <dt>
              <i class="icon-user" />
              <span class="txt">모집인원</span>
            </dt>

            <dd>3/5</dd>
          </dl>
        </div>
      </div>
    </section>

    <section class="section-introduce">
      <p class="title">여행소개</p>

      <div class="cont">소개</div>
    </section>

    <section class="section-member">
      <p class="title">여행멤버</p>

      <div class="cont">
        <div class="list">
          <div class="list-item">
            <button type="button" class="btn-detail" @click="modal.modalOpen()">
              <div class="top">
                <div class="profile">
                  <div class="profile-img"></div>
                </div>

                <div class="user">
                  <div class="user-name">홍길동</div>
                  <div class="user-age">20대</div>
                  <div class="user-gender">여자</div>
                </div>

                <i class="icon-chevron-right" />
              </div>

              <div class="introduce">
                안녕하세요.
              </div>
            </button>
          </div>
        </div>
      </div>
    </section>

    <section class="section-comment">
      <p class="title">댓글</p>

      <div class="cont">
        <CommonCommentForm />
        <CommonCommentList />
      </div>
    </section>
  </div>

  <!-- 맴버 정보 -->
  <CommonModal ref="modal">
    <template #title>홍길동</template>

    <template #default>
      <div>유저 정보</div>
    </template>
  </CommonModal>
</template>

<script setup>
const modal = ref();
</script>

<style lang="scss" scoped>
  .section-area {
    .section {
      &-thumb {
        margin: 0 auto;
        max-width: 1920px;

        .thumb {
          width: 100%;
          height: 400px;
          
          &-img {
            width: 100%;
            height: 100%;
            background: #F8f8f8;
          }
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

      &-schedule {
        margin: 50px auto 0;
        max-width: 1200px;

        & > .title {
          margin-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
        }

        & > .cont {
          .info {
            display: flex;
            flex-direction: column;
            gap: 10px;

            &-item {
              display: flex;
              gap: 10px;

              & > dt {
                min-width: 100px;

                & > i {
                  margin-right: 6px;
                }
              }
            }
          }
        }
      }

      &-introduce {
        margin: 50px auto 0;
        max-width: 1200px;

        & > .title {
          margin-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
        }
      }

      &-member {
        margin: 50px auto 0;
        max-width: 1200px;

        & > .title {
          margin-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
        }

        & > .cont {
          .list {
            display: flex;
            flex-direction: column;
            gap: 30px;

            &-item {
              padding: 20px 30px;
              background: #f8f8f8;
              border-radius: 12px;

              .btn-detail {
                width: 100%;
                text-align: start;
              }

              .top {
                display: flex;
                align-items: center;
                gap: 20px;
                padding-bottom: 20px;

                .profile {
                  width: 80px;
                  height: 80px;
                  border-radius: 50%;
                  overflow: hidden;

                  &-img {
                    width: 100%;
                    height: 100%;
                    background: #d7d7d7;
                  }
                }

                .user {
                  display: flex;
                }
              }

              .icon-chevron-right {
                margin-left: auto;
              }

              .introduce {
                padding-top: 20px;
                border-top: 1px solid #d7d7d7;
              }
            }
          }
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
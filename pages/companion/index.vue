<template>
  <section>
    <div class="left-area">
      <ul class="menu">
        <li class="menu-item" v-for="(location, locationIdx) in locations" :key="locationIdx">
          <button type="button">{{ location?.TEXT }}</button>
        </li>
      </ul>
    </div>

    <div class="right-area">
      <div class="list">
        <div class="list-item" v-for="(item, i) in 5" :key="i">
          <NuxtLink to="/companion/1">
            <div class="thumb">
              <div class="thumb-default"></div>
            </div>

            <div class="info">
              <div class="info-title">제목</div>

              <div class="info-location">
                <i class="icon-fill-pin" />
                <span class="txt">위치</span>
              </div>

              <div class="detail">
                <dl class="detail-item">
                  <dt>모집기간</dt>
                  <dd>2024.07.07 ~ 2024.07.08</dd>
                </dl>

                <dl class="detail-item">
                  <dt>모집인원</dt>
                  <dd>3 / 5</dd>
                </dl>
              </div>

              <div class="info-tag">
                <div class="info-tag-item" v-for="i in 4" :key="i">#20대 여자</div>
              </div>

              <div class="flex-box">
                <div class="info-user">
                  <div class="profile">
                    <div class="profile-img"></div>
                  </div>

                  <div class="user-name">홍길동</div>
                  <div class="user-mbti">isfp</div>
                </div>

                <div class="info-date">2024.07.07</div>
              </div>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const locations = ref([
  { TEXT: '전체', CODE: 'all' },
  { TEXT: '서울', CODE: 'seoul' },
  { TEXT: '부산', CODE: 'busan' },
  { TEXT: '대구', CODE: 'daegu' },
  { TEXT: '인천', CODE: 'incheon' },
  { TEXT: '광주', CODE: 'gwangju' },
  { TEXT: '대전', CODE: 'daejeon' },
  { TEXT: '울산', CODE: 'ulsan' },
  { TEXT: '세종', CODE: 'sejong' },
  { TEXT: '경기', CODE: 'gyeonggi' },
  { TEXT: '강원', CODE: 'gangwon' },
  { TEXT: '충북', CODE: 'chungbuk' },
  { TEXT: '충남', CODE: 'chungnam' },
  { TEXT: '경북', CODE: 'gyeongbuk' },
  { TEXT: '경남', CODE: 'gyeongnam' },
  { TEXT: '전북', CODE: 'jeonbuk' },
  { TEXT: '전남', CODE: 'jeonnam' },
  { TEXT: '제주', CODE: 'jeju' },
]);
</script>

<style lang="scss" scoped>
section {
  display: flex;
  gap: 60px;
  margin: 0 auto;
  max-width: 1200px;

  .left-area {
    width: 360px;

    .menu {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;

      &-item {
        height: 34px;
        line-height: 32px;
        border: 1px solid #d7d7d7;
        text-align: center;
        border-radius: 4px;
        transition: all ease .3s;

        &:hover {
          color: var(--primary-color);
          border-color:var(--primary-color);
        }
      }
    }
  }

  .right-area {
    flex: 1;

    .list {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 40px 24px;

      &-item {
        width: 100%;

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
          border-radius: 12px;
          overflow: hidden;

          &-img {
            width: 100%;
            height: 100%;
          }

          &-default {
            position: relative;
            width: 100%;
            height: 100%;
            background: #eee;

            &:before {
              position: absolute;
              top: 50%;
              left: 50%;
              transform: translate(-50%, -50%);
              content: "\e92f";
              font-family: iconFont;
              font-size: 70px;
              color: #FFF;
            }
          }
        }

        .info {
          padding-top: 20px;

          &-title {
            font-size: 20px;
            font-weight: bold;
            transition: all ease .3s;
          }

          &-tag {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 14px;

            &-item {
              padding: 4px 8px;
              font-size: 14px;
              background: #eee;
              border-radius: 4px;
            }
          }

          &-location {
            & > i {
              margin-right: 4px;
              font-size: 14px;
            }

            .txt {
              font-size: 14px;
            }
          }

          .detail {
            margin-top: 14px;
            
            &-item {
              display: flex;
              align-items: center;
              gap: 10px;
            }
          }

          .flex-box {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 20px;
          }

          &-date {
            font-size: 14px;
          }

          &-user {
            display: flex;
            align-items: center;
            gap: 4px;

            .profile {
              width: 30px;
              height: 30px;
              border-radius: 50%;
              overflow: hidden;

              &-img {
                width: 100%;
                height: 100%;
                background: #d7d7d7;
              }
            }

            .user {
              &-name,
              &-mbti {
                font-size: 14px;
              }
            }
          }
        }
      }
    }
  }
}
</style>
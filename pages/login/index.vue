<template>
  <div class="login">
    <div class="login-wrap">
      <div class="title">
        <div class="txt">로그인</div>
        <div class="desc">로그인을 통해 더 많은 서비스를 이용해 보세요.</div>
      </div>

      <div class="login-form">
        <div class="login-form-item">
          <i class="icon-user"></i>
          <input type="text" placeholder="아이디" />
        </div>

        <div class="login-form-item">
          <i class="icon-lock"></i>
          <input type="password" placeholder="비밀번호" />
        </div>
      </div>

      <button type="button" class="btn-f-fill-main btn-login" title="로그인">로그인</button>

      <div class="find">
        <ul class="find-list">
          <li class="find-list-item">
            <NuxtLink to="/" title="비밀번호 찾기">비밀번호 찾기</NuxtLink>
          </li>

          <li class="find-list-item">
            <NuxtLink to="/" title="아이디 찾기">아이디 찾기</NuxtLink>
          </li>

          <li class="find-list-item">
            <NuxtLink to="/" title="회원가입">회원가입</NuxtLink>
          </li>
        </ul>
      </div>

      <div class="login-other">
        <a id="kakao-login-btn" @click="kakaoLogin" href="javascript:void(0)">
          <img src="https://k.kakaocdn.net/14/dn/btroDszwNrM/I6efHub1SN5KCJqLm1Ovx1/o.jpg" width="222"
               alt="카카오 로그인 버튼" />
        </a>
        <p id="token-result"></p>
      </div>
    </div>
  </div>
</template>

<script setup>
const router = useRouter();

// https://innovation123.tistory.com/181 참고
const kakaoLogin = () => {
  let restApiKey = '자신 api키';
  let redirectUrl = 'http://localhost:3000/callback/kakao';
  const url = new URL('https://kauth.kakao.com/oauth/authorize?response_type=code&client_id=' + restApiKey + "&redirect_uri=" + redirectUrl);

  const screenWidth = window.screen.width;
  const screenHeight = window.screen.height;

  const width = 390;
  const height = 500;
  const left = (screenWidth / 2) - (width / 2);
  const top = (screenHeight / 2) - (height / 2);

  const options = `toolbar=no,scrollbars=no,resizable=no,status=no,menubar=no,width=${width},height=${height},top=${top},left=${left}`;

  window.open(url, '_blank', options);
}
</script>

<style scoped lang="scss">
@import url('~/assets/scss/pages/login.scss');
</style>
<template>
  <div class="header">
    <div class="nav">
      <div class="logo">
        <img src="../assets/logo.svg" alt="logo">
      </div>
      <div class="posts">
        <router-link to="/">
          Posts
        </router-link>
      </div>
      <div class="login">
        <button>
          login
        </button>
      </div>
    </div>
    <div class="background">
      <div
        v-for="i in [1, 2, 3, 4, 5, 6]"
        :key="i" 
        :class="`bubble b-${i}`"
      ></div>
    </div>
  </div>
</template>

<style lang="scss">
  
.header {
  height: 60px;
  .nav {
    width: 75vw;
    height: 43px;
    display: flex;
    margin: auto;
    position: relative;
    top: 13px;

    .logo {
      position: relative;
      width: 20%;
      display: flex;

      img {
        width: 100%;
        height: auto;
      }
    }

    .posts {
      a {
        text-decoration: none;
        display: flex;
        height: 100%;
        align-items: center;
        margin-left: 2rem;
        color: #FFF;
      }
    }

    .login {
      margin-left: auto;

      button {
        color: #5E72E4;
        padding: .5rem 2rem;
        height: 100%;
        border: none;
        border-radius: 5px;
        font-size: 1.05rem;
        cursor: pointer;
      }
    }
  }
  
  .background {
    position: absolute;
    bottom: 54.63%;
    background: linear-gradient(340.03deg, #8DDAD5 8.42%, #00CDAC 91.45%);
    z-index: -1;
    transform: rotateZ(-1deg);
    width: 102vw;
    left: -1vw;
    top: -3vh;

    .bubble {
      background: #FFFFFF;
      mix-blend-mode: normal;
      opacity: 0.1;
      border-radius: 50%;
      position: absolute;
      width: 100px;
      height: 100px;

      &.b-1 {
        top: -11px;
        left: -58px;
      }

      &.b-2 {
        top: 200px;
        left: -6px;
      }

      &.b-3 {
        width: 140px;
        height: 140px;
        top: 224px;
        left: 155px;
        opacity: .15;
      }

      &.b-4 {
        top: 318px;
        right: 165px;
      }

      &.b-5 {
        top: 251px;
        right: 140px;
      }

      &.b-6 {
        top: 59px;
        right: 150px;
      }

      &.b-7 {
        top: 90px;
        right: 400px;
      }
    }
  }
}
</style>
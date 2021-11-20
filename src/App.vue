<template>
  <div id="app">
    <div class="header">
      <div class="nav">
        <div class="logo">
          <img src="../src/assets/logo.svg" alt="logo">
        </div>
        <div class="posts">
          <a href="#">
            Posts
          </a>
        </div>
        <div class="login">
          <button>
            login
          </button>
        </div>
      </div>
      <div class="background">
        <div class="bubble b-1"></div>
        <div class="bubble b-2"></div>
        <div class="bubble b-3"></div>
        <div class="bubble b-4"></div>
        <div class="bubble b-5"></div>
        <div class="bubble b-6"></div>
        <div class="bubble b-7"></div>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
body {
  width: 100vw;
  overflow-x: hidden;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.header {
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

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

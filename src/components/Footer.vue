<template>
  <div class="footer">
    <div class="row top">
      <div class="info">
        <div class="thanks">
          Thank you for supporting us!
        </div>
        <div class="lets">
          Let's get in touch on any of these platforms.
        </div>
      </div>
      <div class="links">
        <a 
          v-for="(social, index) in socialLinks"
          :key="index"
          :class="'link ' + social.name"
        >
          <div class="follow-us">
            follow us
          </div>
          <i :class="social.logo + ' ' + social.name"></i>
        </a>
      </div>
    </div>
    <div class="row bottom">
      <div class="copyright">
        &#169; 2018 <span class="company">Şikayetvar</span>
      </div>
      <div class="alt-link">
        <router-link class="posts" to="/">
          Posts
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      socialLinks: [
        {
          name: 'twitter',
          logo: 'fab fa-twitter-square'
        },
        {
          name: 'facebook',
          logo: 'fab fa-facebook-square'
        },
        {
          name: 'dribbble',
          logo: 'fab fa-dribbble-square'
        },
        {
          name: 'github',
          logo: 'fab fa-github-square'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  
.footer {
  position: absolute;
  bottom: 15px;
  width: 100%;
  height: 204px;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;

  .row {
    display: block;
    width: 75vw;

    &.top {
      border-bottom: 1px solid #aaa;
      padding-bottom: 2rem;
    }

    .info {
      float: left;

      .thanks {
        color: #00CDAC;
        // font-size: 24px;
        font-size: 1.25rem;
        line-height: 3rem;
      }

      .lets {
        color: #32325D;
        // font-size: 22px;
        font-size: 1.20rem;
        line-height: 3rem;
      }
    }

    .links {
      float: right;
      display: flex;
      margin: 1.5rem 0;

      a {
        width: 32px;
        height: 32px;
        margin: 0 .3rem;
        cursor: pointer;
        position: relative;

        &:hover {
          & > .follow-us {
            z-index: 1;
            opacity: 1;
          }
        }

        .follow-us {
          display: flex;
          z-index: -1;
          opacity: 0;
          transition: 200ms ease-out;
          white-space: nowrap;
          background-color: #212529;
          color: #FFF;
          width: 55px;
          left: -15px;
          top: -1.75rem;
          position: absolute;
          border-radius: 5px;
          padding: 0.3rem .2rem;
          font-size: .75rem;
          justify-content: center;

          &::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 10px;
            bottom: -10px;
            left: 20px;
            background-color: #212529;
            clip-path: polygon(0 0, 50% 100%, 100% 0);
          }
        }
        
        i {
          font-size: 2rem;

          &.twitter {
            color: #1DA1F2;
          }

          &.facebook {
            color: #3B5999;
          }

          &.dribbble {
            color: #EA4C89;
          }

          &.github {
            color: #222222;
          }
        }
      }
    }

    .copyright {
      float: left;
      font-weight: bolder;
      font-size: .8rem;
      
      .company {
        color: #00CDAC
      }
    }

    .alt-link {
      float: right;
      
      a {
        color: #8898AA;
        text-decoration: none;
      }
    }

  }
}
</style>
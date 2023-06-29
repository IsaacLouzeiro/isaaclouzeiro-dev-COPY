<script setup lang="ts">
  interface HomeList {
    name: string;
    icon: string; 
    link: string;
  }

  defineProps({
    navItems: {
      type: Array as () => HomeList[],
      required: true
    }
  })
</script>

<template>
  <nav class="d-flex flex-column align-items-center justify-content-between h-100 py-3 mx-md-2 mx-0">
    <!-- link with logo -->
    <router-link to="/" class="d-none d-md-inline-block">
      <img src="../../assets/img/logo.png" alt="Logo" class="img-fluid">
    </router-link>

    <!-- navbar -->
    <ul class="nav flex-column d-none d-md-flex">
      <li 
        v-for="(item, index) in navItems"
        :key="index"
        class="nav-item"
      >
        <a :href="`#${item.link}`" class="btn">
          <font-awesome-icon :icon="`fa-solid ${item.icon}`" />
        </a>

        <span>{{ item.name }}</span>
      </li>
    </ul>

    <!-- object to align navbar -->
    <div class="d-none d-md-block"><br><br><br></div>

    <!-- navbar mobile button -->
    <button class="btn d-inline-block d-md-none btn-bars p-0 m-0" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasExample" aria-controls="offcanvasExample">
      <font-awesome-icon :icon="['fas', 'bars']" />
    </button>

    <!-- navbar mobile -->
    <div class="offcanvas offcanvas-start" tabindex="-1" id="offcanvasExample" aria-labelledby="offcanvasExampleLabel">
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasExampleLabel">language</h5>
        <button type="button" class="btn" data-bs-dismiss="offcanvas" aria-label="Close"><svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg></button>
      </div>
      <div class="offcanvas-body px-3">
        <ul class="nav flex-column">
          <li 
            v-for="(item, index) in navItems"
            :key="index"
            class="nav-item"
          ><a :href="`#${item.link}`" class="nav-link"><font-awesome-icon :icon="`fa-solid ${item.icon}`" />{{ item.name }}</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style lang="scss">
  @import '../../assets/colors.scss';

  .img-fluid {
    width: 60px;
  }

  nav {
    width: 70px;
    position: relative;

    @media only screen and (max-width: 767px) {
      position: absolute;
    }

    .btn-bars {
      svg {
        font-size: 2rem;
        color: $color-l-1;
      }
    }

    .offcanvas {
      background-color: $color-d-1;
      color: $color-l-1;

      .offcanvas-body {
        .nav {
          .nav-item {
             margin: .3rem 0;

             .nav-link {
              padding-left: 0;
              padding-right: 0;
              color: $color-l-1;
              text-decoration: underline;
              text-decoration-color: $color-l-2;

              svg {
                font-size: 1.4rem;
                padding-right: .5rem;
              }
             }
          }
        }
      }
    }
    
    ul {

      li {
        margin: .5rem 0;
        position: relative;

        a.btn {
          width: 3.4rem;
          height: 3rem;
          display: flex;
          justify-content: center;
          align-items: center;
          border: none;
          background-color: rgba($color-l-1, .5);
          color: $color-d-2;
          position: relative;
          z-index: 1;

          &:hover,
          &.active {
            background-color: $color-d-2;
            color: $color-l-1;
          }

          svg {
            font-size: 1.4rem;
          }
        }

        a:hover ~ span {
            opacity: 1;
            left: 115%;
        }

        span {
          opacity: 0;
          display: inline-block;
          position: absolute;
          left: 0;
          top: 20%;
          background-color: $color-d-2;
          padding: .2rem 1rem;
          border-radius: .2rem;
          transition: all .5s;
          z-index: 0;
        }
      }
    }
  }
</style>
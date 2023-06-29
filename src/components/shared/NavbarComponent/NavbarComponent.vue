<script setup lang="ts">
import ButtonNavbarComponent from './ButtonNavbarComponent.vue';

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
    <router-link to="/" class="d-none d-sm-inline-block">
      <img src="../../../assets/img/logo.png" alt="Logo" class="img-fluid">
    </router-link>

    <!-- navbar -->
    <ul class="nav flex-column d-none d-sm-flex">
      <ButtonNavbarComponent 
        v-for="(item, index) in navItems"
        :key="index"
        :name="item.name"
        :icon="item.icon"
        :link="item.link"
      />
    </ul>

    <!-- object to align navbar -->
    <div class="d-none d-sm-block"><br><br><br></div>

    <!-- navbar mobile button -->
    <button class="btn d-inline-block d-sm-none btn-bars p-0 m-0" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasExample" aria-controls="offcanvasExample">
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
  @import '../../../assets/colors.scss';

  .img-fluid {
    width: 60px;
  }

  nav {
    width: 70px;
    position: relative;

    @media only screen and (max-width: 575.98px) {
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
  }
</style>
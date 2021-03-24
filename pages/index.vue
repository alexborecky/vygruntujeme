<template>
  <div class="hero flex">
      <a href="https://vygruntujeme-eshop.cz/" target="_blank" class="half-width flex column middle e-shop">
        <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/store_p12jEIESnkrE.png" alt="">
        <div class="title flex column center">
          <img src="@/assets/images/e-shop.svg" alt="">
          <!-- <h1>E-shop</h1> -->
          <button>
            Do e-shopu
            <div class="underline"></div>
          </button>
        </div>
      </a>
      <nuxt-link to="uklid" class="half-width column middle flex service">
        <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/hero-image_ngDY3IeJQLCU.svg" alt="">
        <div class="title flex column center">
          <img src="@/assets/images/logo.svg" alt="">
          <!-- <h1>Úklid</h1> -->
          <button>
            Vstoupit
            <div class="underline"></div>
          </button>
        </div>
      </nuxt-link>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  async asyncData({$content}) {
        const reviews = await $content('reviews').fetch();
        const services = await $content('services').fetch();
        const adv = await $content('advantages').fetch();
        const partners = await $content('partners').fetch();
        return {
          reviews,
          services,
          adv,
          partners,
        }
      },
  components: {
    Logo
  }
}
</script>

<style lang="scss" scoped>

.hero {
  height: 100vh;
  .half-width {
    height: 100%;
    img {
      max-width: 400px;
      margin: 40px;
    }
    &:first-child {
      border-right: 2px solid rgba($color: $main-orange, $alpha: .08);
    }
    &:hover {
      background-color: lighten($color: $main-orange, $amount: 40);
      border: white;
      .underline {
        width: 100%;
      }
    }
    @media (max-width: 800px) {
      img {
        max-width: 240px;
      }
    }
  }
  a {
      color: black;
  }
  @media (max-width: 650px) {
      flex-flow: column;
      .half-width {
        width: 100%;
        img {
          max-width: 200px;
          margin: 16px;
        }
      }
  }
  @media (max-width: 400px) {
      .half-width {
        img {
          max-width: 160px;
          margin: 16px;
        }
      }
  }
}

button {
  border: none;
  background: none;
  font-size: 24px;
  font-weight: 600;
  color: $main-orange;
  .underline {
    width: 0%;
    height: 4px;
    background-color: $main-orange;
    transition: .2s ease-in-out;
  }
  &:hover {
    cursor: pointer;
  }
  @media (max-width: 650px) {
    font-size: 16px;
  }
}

</style>

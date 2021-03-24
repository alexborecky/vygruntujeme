<template>
  <div class="hero flex">
      <a href="https://vygruntujeme-eshop.cz/" target="_blank" class="half-width flex column middle e-shop">
        <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/store_p12jEIESnkrE.png" alt="">
        <img src="@/assets/images/e-shop.svg" alt="">
        <!-- <h1>E-shop</h1> -->
      </a>
      <nuxt-link to="uklid" class="half-width column middle flex service">
        <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/hero-image_ngDY3IeJQLCU.svg" alt="">
        <img src="@/assets/images/logo.svg" alt="">
        <!-- <h1>Úklid</h1> -->
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
    &:hover {
      background-color: lighten($color: $main-orange, $amount: 40);
    }
  }
  a {
      color: black;
  }
}

</style>

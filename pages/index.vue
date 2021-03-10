<template>
  <div class="hero main">
    <img class="image-arc" src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/background_Qq5vbtHx7hJAf.png" alt="">
    <div class="container">
      <div class="value-proposition hero flex column center">
        <div class="text flex column center">
          <h1>Profesionálové</h1>
          <p class="bigger">Chytrý úklid Vaší firmy.</p>
          <PrimaryButton 
            link="/"
            content="Chci uklidit!"
          />
        </div>
        <div class="illustration flex middle">
          <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/hero-image_ngDY3IeJQLCU.svg" alt="">
        </div>
      </div>
      <div class="reviews hero flex column center id-section">
        <h2 class="flex column center">Řekli o nás <div class="underline"></div></h2>
        <div class="review-container flex column full-width">
          <Review 
            v-for="review in reviews.reviews" 
            :key="review.name"
            :image="review.image"
            :name="review.name"
            :title="review.title"
            :review="review.review"
          />
        </div>
      </div>
      <div class="services hero flex column center full-width id-section">
        <h2 class="flex column center">Uklízíme, dezinfikujeme, umíme <div class="underline"></div></h2>
        <div class="badge-container middle flex full-width">
          <Badge 
            v-for="service in services.services" :key="service.service"
            :image="service.image"
            :service="service.service"
          />
        </div>
      </div>
      <div class="advantages hero flex column center full-width id-section">
        <h2 class="flex column center">Vaše výhody <div class="underline"></div></h2>
        <div class="advantage-container flex column middle">
          <Advantage 
            v-for="adv in adv.advantages" :key="adv.title"
            :img="adv.img"
            :title="adv.title"
            :text="adv.text"
          />
        </div>
      </div>
      <div class="partners flex column center full-width id-section">
        <h2 class="flex column center">Naši partneři <div class="underline"></div></h2>
        <div class="logo-container flex center">
          <img 
            v-for="partners in partners.logos" :key="partners"
          :src="partners.logo" alt="">
        </div>
      </div>
    </div>
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

<style lang="scss">

.main {
  .id-section {
    margin: 120px 0;
  }
  .image-arc {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    z-index: -1;
  }
  .value-proposition {
    height: 80vh;
    justify-content: space-between;
    .text {
      margin-top: 8%;
    }
    .illustration {
      height: 72%;
      img {
        height: 100%;
      }
    }
  }
  .reviews {
    margin-top: 20vh;
    .review:first-child {
      margin-top: 120px;
    }
    .review:last-child {
      margin-bottom: 120px;
    }
    .review:nth-child(even) {
      align-self: flex-end;
    }
  }
  .services {
    margin-top: 80px;
    flex-wrap: wrap;
    .badge-container {
      margin-top: 80px;
      flex-wrap: wrap;
    }
  }
  .advantages {
    .advantage-container {
      margin-top: 40px;
    }
    .advantage:nth-child(odd) {
      align-self: flex-end;
    }
    .advantage:nth-child(even) {
      align-self: flex-start !important;
      justify-content: flex-end;
      img {
        order: 2;
      }
      .content {
        order: 1;
        text-align: right;
      }
    }
  }
  .partners {
    .logo-container {
      margin-top: 80px;
      flex-wrap: wrap;
      justify-content: center;
      img {
        width: 240px;
        margin: 24px;
        filter: grayscale(100%)
      }
    }
  }
}

</style>

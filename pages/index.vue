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
          <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/illustration1_6o4KEWzF4lEpG.png" alt="">
        </div>
      </div>
      <div class="reviews hero flex column center">
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
      <div class="services hero flex column center full-width">
        <h2 class="flex column center">Uklízíme, dezinfikujeme, umíme <div class="underline"></div></h2>
        <div class="badge-container middle flex full-width">
          <Badge 
            v-for="service in services.services" :key="service.service"
            :image="service.image"
            :service="service.service"
          />
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
        return {
          reviews,
          services
        }
      },
  components: {
    Logo
  }
}
</script>

<style lang="scss">

.main {
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
}

</style>

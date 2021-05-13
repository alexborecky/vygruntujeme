<template>
  <div class="hero main">
    <div class="image-arc">
      <img src="https://ik.imagekit.io/alexborecky/CzechCon/vygruntujeme/background_Qq5vbtHx7hJAf.png" alt="">
    </div>
    <div class="container">
      <div class="value-proposition hero flex column center">
        <div class="text flex column center">
          <h1>Profesionálové</h1>
          <p class="bigger">Chytrý úklid Vaší firmy.</p>
          <PrimaryButton 
            link="#kontakt"
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
      <div class="contact flex column center full-width id-section" id="kontakt">
        <h2 class="flex center column">Kontaktujte nás <div class="underline"></div></h2>
        <a class="email" href="mailto:info@vygruntujeme.cz">info@vygruntujeme.cz</a>
      </div>
    </div>
    <footer class="flex full-width column id-section">
      <div class="container flex">
        <img src="@/assets/images/logo.svg" alt="">
        <div class="about">
          <h3>O nás</h3>
          <ul>
            <!-- <li><nuxt-link to="/dezinfekce">Dezinfekce</nuxt-link></li> -->
            <li>
              <a class="flex center" target="blank" href="https://vygruntujeme-eshop.cz">
                        E-shop 
                        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M4 12L12 4" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        <path d="M5.5 4H12V10.5" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </a></li>
          </ul>
        </div>
        <div class="footer-contact">
          <h3>Kontakt</h3>
          <ul>
            <li><a class="email" href="mailto:info@vygruntujeme.</li>cz">info@vygruntujeme.cz</a>
            <li><a class="email" href="tel:+420123456789">+420 123 456 789</a></li>
          </ul>
        </div>
      </div>
      <div class="rights">
        <p>2021 © vygruntujeme - Všechna práva vyhrazena, Created by <a href="">Alex Borecký</a></p>
      </div>
    </footer>
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

.main {
  .id-section {
    margin: 120px 0;
    @media only screen and (max-width: 720px) {
      margin: 64px 0;
    }
  }
  .image-arc {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    z-index: -1;
    img {
      height: 100%;
      width: 100%;
    }
    @media only screen and (max-width: 650px) {
      background-color: lighten($color: $main-orange, $amount: 40%);
      img {
        display: none;
      }
    }
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
    @media only screen and (max-width: 1024px) {
      .illustration {
        width: 100%;
        img {
          width: 100%;
        }
      }
    }
    @media only screen and (max-width: 780px) {
      .text {
        margin-top: 20%;
      }
    }
    @media only screen and (max-width: 450px) {
      .illustration {
        width: 100%;
        img {
          width: 100%;
        }
      }
      .text {
        margin-top: 50%;
      }
    }
    @media only screen and (max-width: 320px) {
      .text {
        margin-top: 50%;
      }
    }
  }
  .reviews {
    margin-top: 20vh;
    @media only screen and (max-width: 960px) {
        margin-top: 25vh !important;
    }
    .review:first-child {
      margin-top: 120px;
      @media only screen and (max-width: 960px) {
        margin-top: 0px;
      } 
    }
    .review:last-child {
      margin-bottom: 120px;
      @media only screen and (max-width: 960px) {
        margin-bottom: 0;
      }
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
        order: 2 !important;
      }
      .content {
        order: 1 !important;
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
        max-width: 240px;
        max-height: 80px;
        margin: 24px;
        filter: grayscale(100%)
      }
    }
    @media only screen and (max-width: 550px) {
      .logo-container {
        img {
          max-height: 56px;
        }
      }
    }
  }
  .contact {
    .email {
      font-size: 40px;
      color: $main-orange;
      margin-top: 80px;
      &:hover {
        color: darken($color: $main-orange, $amount: 10%) !important;
      }
    }
    @media only screen and (max-width: 550px) {
      .email {
        font-size: 16px;
        margin-top: 40px;
      }
    }
  }
  footer {
    background-color: lighten($color: $main-orange, $amount: 40%);
    height: 400px;
    margin-bottom: 0px !important;
    justify-content: center;
    align-items: center;
    position: relative;
    .container {
      justify-content: space-between;
      height: 50%;
    }
    img {
      height: 48px;
    }
    ul {
      padding-left: 0;
      list-style: none;
      margin-top: 24px;
      li {
        margin: 8px 0;
      }
      a {
        color: rgba($color: $main-black, $alpha: .72)
      }
    }
    .about {
      a {
        svg {
          margin-left: 8px;
          path {
            transition: .3s ease-in-out;
          }
        }
        &:hover {
          svg {
            path {
              stroke: $main-orange;
            }
          }
        }
      }
    }
    .rights {
      position: absolute;
      bottom: 16px;
      p, a {
        font-size: 10px;
        letter-spacing: .2px;
        color: $main-black;
      }
    }
    @media only screen and (max-width: 960px) {
      height: auto;
      .container {
        flex-flow: column;
        justify-content: center;
        align-items: center;
        margin: 40px 0;
        .about, .footer-contact {
          text-align: center;
          margin: 24px 0;
        }
      }
      .rights {
          max-width: 240px;
          text-align: center;
          p {
            line-height: 16px !important;
          }
      }
    }
  }
  @media only screen and (max-width: 720px) {
      .badge-container, .advantage-container, .review-container, .logo-container {
        margin-top: 40px !important;
      }
    }
}

</style>

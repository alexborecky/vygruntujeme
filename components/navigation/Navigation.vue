<template>
    <div class="navigation full-width flex" :class="{'hidden-navbar': !showNavbar, colour: !transparent, scrolled: !scrolledNav}">
        <div class="container flex">
            <nuxt-link to="#home" class="logo">
                <div>
                    <img src="@/assets/images/logo.svg" alt="">
                </div>
            </nuxt-link>
            <ul class="flex center links">
                <li
                    v-for="item in items" 
                    :key="item.link"
                >
                    <nuxt-link 
                        :to="item.link">
                        {{item.title}}
                        <div class="underline"></div>
                    </nuxt-link>
                </li>
                <li>
                    <a class="flex center" target="blank" href="https://vygruntujeme-eshop.cz">
                        E-shop 
                        <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M4 12L12 4" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        <path d="M5.5 4H12V10.5" stroke="black" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import items from '@/assets/data/navigation.js'
const OFFSET = 60
    export default {
        name: 'Navigation',
        data () {
            return {
                items: items,
                showNavbar: true,
                scrolledNav: true,
                lastScrollPosition: 0,
                scrollValue: 0,
                transparent: false
            }
        },
        mounted () {
            this.lastScrollPosition = window.pageYOffset
            window.addEventListener('scroll', this.onScroll)
            // const viewportMeta = document.createElement('meta')
            // viewportMeta.name = 'viewport'
            // viewportMeta.content = 'width=device-width, initial-scale=1'
            // document.head.appendChild(viewportMeta)
        },

        beforeDestroy () {
            window.removeEventListener('scroll', this.onScroll)
        },
        methods: {
            onScroll () {
                if (window.pageYOffset < 0) {
                    return
                }
                if (Math.abs(window.pageYOffset - this.lastScrollPosition) < OFFSET) {
                    return 
                }
                this.showNavbar = window.pageYOffset < this.lastScrollPosition
                this.scrolledNav = window.pageYOffset < this.lastScrollPosition
                this.transparent = window.pageYOffset > 400
                this.lastScrollPosition = window.pageYOffset
            },
        }
    }
</script>

<style lang="scss" scoped>

.navigation {
    position: sticky;
    height: 80px;
    z-index: 100;
    top: 0;
    margin-top: 40px;
    background-color: white;
    transition: .4s ease-in-out;
    .container {
        height: 100%;
        justify-content: space-between;
        align-items: center;
        .logo {
            img {
                height: 40px;
            }
        }
        ul {
            // height: 100%;
            padding-left: 0;
            list-style: none;
            a {
                list-style: none;
                margin-left: 56px;
                color: black;
                position: relative;
                font-weight: 500;
                .underline {
                    transition: .3s ease-in-out;
                    height: 4px;
                    width: 0%;
                    background-color: $main-orange;
                    position: absolute;
                    left: 0;
                    margin-top: 4px;
                    border-radius: 4px;
                }
                &:hover {
                    .underline {
                        width: 100%;
                    }
                    svg {
                        path {
                            stroke: $main-orange;
                        }
                    }
                }
                svg {
                    margin-left: 8px;
                    path {
                        transition: .3s ease-in-out;
                    }
                }
            }
        }
    }
    @media only screen and (max-width: 960px) {
        display: none;
    }
}

.colour {
    background-color: transparent;
}

.navigation.hidden-navbar {
  transform: translate3d(0, -140px, 0);
}

</style>
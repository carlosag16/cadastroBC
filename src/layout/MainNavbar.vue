<template>
  <md-toolbar
    id="toolbar"
    md-elevation="0"
    class="md-transparent md-absolute md-white "
    :class="extraNavClasses"
    :color-on-scroll="colorOnScroll"
  >
    <div class="md-toolbar-row md-collapse-lateral">
      <div class="md-toolbar-section-start ">
        <h3 class="md-title " data-toggle="dropdown">
          <img src="../assets/img/Logo_Biblioteca.png" height="35" width="35" />
          <a
            href="http://bc.ufpa.br/"
            style="color: #000 !important; margin-left: 18px "
          >
            Biblioteca Central UFPA</a
          >
        </h3>
      </div>
      <div class="">
        <md-button
          class="md-just-icon md-simple md-toolbar-toggle"
          :class="{ toggled: toggledClass }"
          @click="toggleNavbarMobile()"
        >
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </md-button>

        <div class="md-collapse">
          <div class="md-collapse-wrapper">
            <mobile-menu nav-mobile-section-start="false">
              <!-- Here you can add your items from the section-start of your toolbar -->
            </mobile-menu>
            <md-list>
              <li class="md-list-item" v-if="!showDownload">
                <a
                  href="javascript:void(0)"
                  class="md-list-item-router md-list-item-container md-button-clean dropdown"
                >
                </a>
              </li>

              <li class="md-list-item" v-else>
                <a
                  href="javascript:void(0)"
                  class="md-list-item-router md-list-item-container md-button-clean dropdown"
                >
                </a>
              </li>

              <md-list-item href="/cadastro-bc">
                <p class="lg">Paginal Inicial</p>
                <md-tooltip md-direction="bottom"
                  >Voltar para a pagina inicial
                </md-tooltip>
              </md-list-item>

              <md-list-item href="/cadastro-bc/fale-conosco">
                <p class="lg">Fale Conosco</p>
                <md-tooltip md-direction="bottom">Envie sua dúvida </md-tooltip>
              </md-list-item>

              <md-list-item
                href="https://twitter.com/BibliotecaUfpa"
                target="_blank"
              >
                <i class="fab fa-twitter" style="color:#000"></i>
                <p class="hidden-lg">Twitter</p>
                <md-tooltip md-direction="bottom"
                  >Siga a gente no Twitter</md-tooltip
                >
              </md-list-item>
              <md-list-item
                href="https://www.facebook.com/bcufpa"
                target="_blank"
              >
                <i class="fab fa-facebook-square" style="color:#000"></i>
                <p class="hidden-lg">Facebook</p>
                <md-tooltip md-direction="bottom"
                  >Nos siga no Facebook</md-tooltip
                >
              </md-list-item>
              <md-list-item href="https://instagram.com/bcufpa" target="_blank">
                <i class="fab fa-instagram" style="color:#000"></i>
                <p class="hidden-lg">Instagram</p>
                <md-tooltip md-direction="bottom"
                  >Siga a gente no Instagram</md-tooltip
                >
              </md-list-item>
            </md-list>
          </div>
        </div>
      </div>
    </div>
  </md-toolbar>
</template>

<script>
let resizeTimeout
function resizeThrottler(actualResizeHandler) {
  // ignore resize events as long as an actualResizeHandler execution is in the queue
  if (!resizeTimeout) {
    resizeTimeout = setTimeout(() => {
      resizeTimeout = null
      actualResizeHandler()

      // The actualResizeHandler will execute at a rate of 15fps
    }, 66)
  }
}

import MobileMenu from '@/layout/MobileMenu'
export default {
  components: {
    MobileMenu,
  },
  props: {
    type: {
      type: String,
      default: 'white',
      validator(value) {
        return [
          'white',
          'default',
          'primary',
          'danger',
          'success',
          'warning',
          'info',
        ].includes(value)
      },
    },
    colorOnScroll: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      extraNavClasses: '',
      toggledClass: false,
    }
  },
  computed: {
    showDownload() {
      const excludedRoutes = ['login', 'landing', 'profile']
      return excludedRoutes.every(r => r !== this.$route.name)
    },
  },
  methods: {
    bodyClick() {
      let bodyClick = document.getElementById('bodyClick')

      if (bodyClick === null) {
        let body = document.querySelector('body')
        let elem = document.createElement('div')
        elem.setAttribute('id', 'bodyClick')
        body.appendChild(elem)

        let bodyClick = document.getElementById('bodyClick')
        bodyClick.addEventListener('click', this.toggleNavbarMobile)
      } else {
        bodyClick.remove()
      }
    },
    toggleNavbarMobile() {
      this.NavbarStore.showNavbar = !this.NavbarStore.showNavbar
      this.toggledClass = !this.toggledClass
      this.bodyClick()
    },
    handleScroll() {
      let scrollValue =
        document.body.scrollTop || document.documentElement.scrollTop
      let navbarColor = document.getElementById('toolbar')
      this.currentScrollValue = scrollValue
      if (this.colorOnScroll > 0 && scrollValue > this.colorOnScroll) {
        this.extraNavClasses = `md-${this.type}`
        navbarColor.classList.remove('md-transparent')
      } else {
        if (this.extraNavClasses) {
          this.extraNavClasses = ''
          navbarColor.classList.add('md-transparent')
        }
      }
    },
    scrollListener() {
      resizeThrottler(this.handleScroll)
    },
    scrollToElement() {
      let element_id = document.getElementById('downloadSection')
      if (element_id) {
        element_id.scrollIntoView({ block: 'end', behavior: 'smooth' })
      }
    },
  },
  mounted() {
    document.addEventListener('scroll', this.scrollListener)
  },
  beforeDestroy() {
    document.removeEventListener('scroll', this.scrollListener)
  },
}
</script>

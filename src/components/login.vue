<template></template>

<script type="text/javascript">
  /* eslint-disable */
  import {mapMutations} from 'vuex'
  import Vivus from 'vivus'
  import logoData from './logoData'
  import { Platform } from 'quasar'
  export default {
    mounted () {
      this.setLayoutNeeded(false)
      this.setIsLoginPage(true)
      this.startAnimation()
    },
    beforeDestroy () {
      this.setLayoutNeeded(true)
      this.setIsLoginPage(false)
    },
    computed: {
      heightSize (){
        if (Platform.is.desktop) {
          return 'items-center'
        }
        return ''
      },
      finalBgColor () {
        return `bg-${this.bgColor}-${this.toneColor}`
      },
      logoMethod () {
        return logoData[this.logo]
      }
    },
    data () {
      return {
        logos: Object.keys(logoData),
        logo: 'Digitalizer',
        email: 'quasar@admin.com',
        password: '123456',
        bgColor: 'purple',
        toneColor: 10,
        colors: ['purple', 'blue', 'red', 'green', 'amber'],
        colorTones: ['2', '4', '6', '8', '10'],
        buttonClasses: ['normal','outline', 'clear', 'push', 'bordered', 'round'],
        buttonClass: 'normal',
        vivus: ''
      }
    },
    methods: {
      ...mapMutations(['setLayoutNeeded', 'setIsLoginPage']),
      login () {
        this.setLayoutNeeded(true)
        this.setIsLoginPage(false)
        this.$router.push('/')
      },
      startAnimation () {
        this.vivus = new Vivus('logo', {
            duration: 400,
          forceRender: false
          }, function(element) {
            for (let item of element.el.children[0].children) {
              item.setAttribute('style', 'fill:white')
              item.setAttribute('style', 'fill:white')
            }
          }
        )
      }
    }
  }
</script>
<style scoped>
  .card {
    margin-bottom: 0px;
  }
  .card-content {
    min-height: 160px;
  }
  button {
    margin-bottom: 4%;
  }
  h4 {
    font-weight: 300;
  }
</style>
<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="showAbs" :style="opacityStyle">
      景点详情
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 26) {
        let opacity = top / 26
        console.log(opacity)
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  unmounted () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header-abs
  position absolute
  left .1rem
  top .1rem
  width .75rem
  height .75rem
  line-height .75rem
  text-align center
  border-radius .4rem
  background rgba(0, 0, 0, .5)
  .header-abs-back
    color #ffffff
    font-size .4rem
.header-fixed
  z-index 2
  height $headerHeight
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .32rem
  position fixed
  left 0rem
  right 0rem
  top 0rem
  .header-fixed-back
    width .64rem
    text-align center
    font-size .4rem
    position absolute
    top 0
    left 0
    color #fff
</style>

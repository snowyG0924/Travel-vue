<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right ">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe6aa;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
.header
  display flex
  line-height $headerHeight
  color #fff
  background $bgColor
  .header-left
    width .64rem
    float left
    .back-icon
      text-align center
      font-size .4rem
  .header-right
    min-width 1.04rem
    float right
    text-align center
    color #ffffff
    padding 0 .1rem
    .arrow-icon
      font-size .24rem
      margin-left -.1rem
  .header-input
    flex 1
    height .64rem
    line-height .64rem
    margin-top .12rem
    margin-left .1rem
    padding-left .2rem
    background #fff
    border-radius .1rem
    color #ccc
</style>

<template>
  <div>
    <div class="header">
      城市选择
      <router-link to="/">
        <div class="iconfont city-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
.header
  overflow hidden
  height $headerHeight
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .32rem
  position relative
.city-back
  width .64rem
  text-align center
  font-size .4rem
  position absolute
  top 0
  left 0
  color #fff
</style>

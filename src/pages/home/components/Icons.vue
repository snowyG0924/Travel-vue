<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) in pages" :key="index">
        <div class="icon" v-for="item in page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-cont" :src="item.imgUrl">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
    <div class="swiper-pagination"  slot="pagination"></div>
  </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl'
@import '~styles/mixins.styl'
.wrapper >>> .swiper-pagination-bullet-active
  background $bgColor !important
.wrapper >>> .swiper-pagination-bullet
  margin .1rem
.wrapper >>> .swiper-pagination
  width 100%
  bottom .01rem
  text-align center
.wrapper >>> .swiper-container
  height 0
  padding-bottom 55%
.wrapper
  margin-top .1rem
  position relative
  .icon
    position relative
    overflow hidden
    float left
    width 25%
    padding-bottom 25%
    .icon-img
      position absolute
      top 0
      left 0
      right 0
      bottom .33rem
      box-sizing border-box
      padding .1rem
      .icon-img-cont
        height 90%
        display block
        margin 0 auto
    .icon-desc
      position absolute
      left 0
      right 0
      bottom 0
      line-height .44rem
      height .44rem
      color $darkTextColor
      text-align center
      ellipsis()
</style>

<template>
  <div>
    <div class="header">
      城市选择
      <router-link to="/">
        <div class="iconfont header-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name:'CityHeader'
}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import '~styles/variables'
  .header
    position relative
    overflow hidden
    height $headerHeight
    line-height $headerHeight
    text-align center
    color #ffffff
    background-color $bgColor
    font-size .32rem
    .header-back
      position absolute
      top 0
      left 0
      width .64rem
      text-align center
      font-size .4rem
      color #fff
</style>

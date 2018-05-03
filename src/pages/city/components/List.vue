<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hot" :key="item.id">
            <div class="button" @click="handleCityClick(item.name)">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area"
        v-for="(item,key) of cities"
        :key="key"
        :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" @click="handleCityClick(innerItem.name)" v-for="innerItem of item" :key="innerItem.id">
            {{innerItem.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapState,mapMutations} from 'vuex'
export default {
  name:'CityList',
  props:{
    cities:Object,
    hot:Array,
    letter:String
  },
  computed:{
    ...mapState({
      currentCity:'city'
    })
  },
  data () {
    return {
    };
  },
  methods:{
    handleCityClick(city){
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  mounted(){
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch:{
    letter (){
      if(this.letter){
        // console.log(this.letter)
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }

}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import '~styles/variables.styl'
    .border-topbottom
      &:before
        border-color #cccccc
      &:after
        border-color #ccc
    .border-bottom
      &:before
        border-color #cccccc
    .list
      overflow hidden
      position absolute
      top 1.58rem
      left 0
      right 0
      bottom 0
      .title
        line-height .54rem
        background-color #eeeeee
        padding-left .2rem
        color #666666
        font-size .26rem
      .button-list
        overflow hidden
        padding .1rem .6rem .1rem .1rem
        .button-wrapper
          float left
          width 33.33%
          .button
            margin .1rem
            padding .1rem 0
            text-align center
            border .02rem solid #cccccc
            border-radius .06rem
      .item-list
        .item
          line-height .76rem
          padding-left .2rem
</style>

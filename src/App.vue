<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/rating">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view :seller="seller"></router-view>
  </div>
</template>

<script>
  import header from './components/header/header'

  export default {
    data () {
      return {
        seller: {}
      }
    },
    created () {
      this.$http.get('/api/seller').then((resp) => {
        // 返回数据
        this.seller = resp.body
      })
    },
    components: {
      'v-header': header
    }
  }
</script>

<style lang="stylus" rel="stylussheet/stylus">
  @import "./common/css/mixin.styl";

  #app
    .tab
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      border-1px(rgba(7, 17, 27, 0.5))

      .tab-item
        flex: 1
        text-align: center

        & > a
          display: block
          font-size: 18px
          color: rgb(77, 85, 93)

          &.active
            color: rgb(240, 20, 20)
</style>

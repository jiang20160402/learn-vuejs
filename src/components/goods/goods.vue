<template>
  <div class="goods">
    <div class="menu-wrapper">
      <ul>
        <li v-for="item in goods" class="menu-item">
            <span class="text border-1px">
              <supporticon v-if="item.type>0" :type="item.type" size="3"></supporticon>
              {{ item.name }}
            </span>
        </li>
      </ul>
    </div>
    <div class="foods-wrapper"></div>
  </div>
</template>

<script>
  import supporticon from '../supports/icon'
  const ERR_OK = 0

  export default {
    props: ['seller'],
    data () {
      return {
        goods: {}
      }
    },
    created () {
      this.fetchdata()
    },
    methods: {
      fetchdata () {
        this.$http.get('/api/goods')
        .then(response => {
          response = response.data
          if (response.errno === ERR_OK) {
            this.goods = response.data
          }
        })
        .catch(err => {
          console.log('get goods error:' + err)
        })
      }
    },
    components: {
      'supporticon': supporticon
    }
  }

</script>

<style lang="stylus">
  @import "../../common/stylus/mixin.styl"

  .goods
    display: flex
    position: absolute
    top: 174px
    bottom: 46px
    width: 100%
    overflow: hidden
    .menu-wrapper
      flex: 0 0 80px
      width: 80px
      background: #f3f5f7
      .menu-item
        display: table
        height: 54px
        width: 56px
        padding: 0 12px
        line-height: 14px
        .icon
          display: inline-block
          width: 12px
          height: 12px
          vertical-align: top
          margin-right: 2px
          background-size: 12px 12px
          background-repeat: no-repeat
        .text
          display: table-cell
          width: 56px
          vertical-align: middle
          border-1px(rgba(7, 17, 27, 0.1))          
          font-size: 12px
    .foods-wrapper
      flex: 1
</style>

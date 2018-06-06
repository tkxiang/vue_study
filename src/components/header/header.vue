<template>
  <div class="header">
    <div class="header-top">
      <div class="avatar">
        <img :src="seller.avatar">
      </div>
      <div class="content">
          <div class="title">
            <span class="brand">品牌</span>
            <span class="name">{{seller.name}}</span>
          </div>
          <div class="description">{{seller.description}}/{{seller.deliveryTime}}</div>
          <div class="seller-support" v-if="seller.supports">
            <span class="icon" :class="classMap[seller.supports[0].type]"></span>
            <span class="text">{{seller.supports[0].description}}</span>
          </div>
          <div class="support-count" @click="detailShow">
            <span class="count">{{seller.supports.length}}</span>个
          </div>
        </div>
    </div>
    <div class="notice">
      <span class="notice-pic"></span>
      <div class="bulletin">
        {{seller.bulletin}}
      </div>
    </div>
    <div class="detail" v-show="showDetail">
      <div class="detail-wrapper">
        <div class="detail-content">

        </div>
      </div>
      <div class="detail-close icon-close" @click="showDetail=false">x</div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        classMap: ['decrease', 'discount', 'special', 'invoice', 'guarantee'],
        showDetail:false
      }
    },
    methods:{
      detailShow:function(){
        this.showDetail = true;
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../../static/sass/mixin";
.header{
  color: #fff;
  background: rgba(7,17,27,0.5);
  .header-top{
    padding: 24px;
    font-size: 0;
    position: relative;
  }
  .avatar{
    width: 64px;
    height: 64px;
    display: inline-block;
    vertical-align: top;
  }
  .content{
    margin-left: 16px;
    display: inline-block;
    .title{
      margin-top: 2px;
      .brand{
        display: inline-block;
        height: 18px;
        line-height: 18px;
        padding: 0 6px;
        margin-right: 6px;
        font-size: 14px;
        font-weight: bold;
        background: #f01414;
      }
      .name{
        font-size: 16px;
        color: rgb(255,255,255);
        font-weight: bold;
        line-height: 18px;
      }
    }
    .description{
      margin-top: 8px;
      font-size: 12px;
    }
    .seller-support{
      margin-top: 10px;
      .icon{
        width: 12px;
        height: 12px;
        vertical-align: top;
        display: inline-block;
        background-size: cover;
        &.decrease{
          @include bg-image('decrease_1')
        }
      }
      .text{
        margin-left: 4px;
        line-height: 12px;
        font-size: 10px;
      }
    }
    .support-count{
      position: absolute;
      right: 12px;
      bottom: 15px;
      height: 24px;
      line-height: 24px;
      padding: 0 8px;
      border-radius: 10px;
      font-size: 10px;
      background: rgba(0,0,0,0.2);
      .count{
        font-size: 10px;
        color: rgb(255,255,255);
      }
    }
  }
  .notice{
    height: 28px;
    line-height: 28px;
    padding: 0 12px;
    background-color: rgba(7,17,27,0.2);
    display: flex;
    .notice-pic{
      width: 22px;
      height: 12px;
      margin-top: 8px;
      display: inline-block;
      vertical-align: top;
      margin-right: 4px;
      @include bg-image('bulletin');
      background-size: contain;
    }
    .bulletin{
      flex: 1;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      font-size: 10px;
    }
  }
  .detail{
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    width: 100%;
    z-index: 200;
    overflow: auto;
    background: rgba(7,17,27,0.8);
    fiter:blur(10px);
    &-wrapper{
      min-height: 100%;
      .detail-content{
        padding-top: 64px;
        padding-bottom: 64px;
      }
    }
    &-close{
      display: block;
      position: relative;
      width: 32px;
      height: 32px;
      line-height: 32px;
      text-align: center;
      font-size: 32px;
      margin: -64px auto 0;
      color: rgba(255,255,255,0.5);
    }
  }
}
</style>

<template>
  <div>
    <v-header></v-header>
    <div class="tab">
      <router-link to="/goods" class="tab-item">商品</router-link>
      <router-link to="/ratings" class="tab-item">评论</router-link>
      <router-link to="/seller" class="tab-item">商家</router-link>
    </div>
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
  </div>
</template>

<script>
  import header from './components/header/header'
  export default{
    components: {
      'v-header': header
    }
  }
</script>

<style lang="scss" scoped>
  @import "../static/sass/mixin";
  .tab{
    display: flex;
    height: 40px;
    line-height: 40px;
    @include border-1px(bottom,#ddd);
    &-item{
      flex:1;
      text-align: center;
      color: #666;
      text-decoration: none;
      &.active{
        color: orange;
      }
    }
  }
</style>

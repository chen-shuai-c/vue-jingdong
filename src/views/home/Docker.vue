<template>
     <div class="docker">
    <div
      v-for=" (item, index) in dockerList "
      :class="{'docker__item': true, 'docker__item--active': index===0}"
      :key="item.icon"
      >
      <div class="iconfont" v-html="item.icon" />
      <div class="docker__title" v-html="item.text" />
    </div>
  </div>
</template>

<script>
export default {
    name: 'Docker',
    setup () {
      const dockerList = [
        { icon: '&#xe619;', text: '首页' },
        { icon: '&#xe638;', text: '购物车' },
        { icon: '&#xe63e;', text: '订单' },
        { icon: '&#xe660;', text: '我的' }
      ]
      return { dockerList }
    }
}
</script>

<style lang="scss" scoped>
@import '../../style/viriables.scss';
@import '../../style/mixins.scss';
.docker{
  display: flex;
  box-sizing: border-box;
  position: absolute;
  padding: 0 .18rem;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 0.49rem;
  border-top: .01rem solid $content-bgcolor;
  color: $content-fontcolor;
  &__item{
    flex: 1;
    text-align: center;
    .iconfont{
      margin: 0.07rem 0 0.02rem 0;
      font-size: .18rem;
    }
    &--active{
      color: #1fa4fc;
    }
  }
  &__title{
    font-size: .2rem;
  transform: scale(.5,.5);
  transform-origin: center top;
  }
}
</style>

<template>
  <div class="header">
    <div class="header-left">
        <i class="iconfont back-icon" >&#xe624;</i>
    </div>
    <div class="header-input">
        <i class="iconfont">&#xe632;</i>
        输入城市/景点/游玩主题</div>
    <div class="header-right">
        {{city}}
        <i class="iconfont arrow-icon">&#xe600;</i>
        </div>
  </div>
</template>
<script>

export default {
  name: 'HomeHeader',
  props:{
    city:String
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header
    display :flex
    height: .86rem
    background: $bgColor
    color:#fff
    line-height .86rem
    .header-left
      width: .64rem
      float:left
      .back-icon
        display :block
        text-align :center
        font-size:.4rem
    .header-input
      flex: 1
      background:#fff
      margin-top:.12rem
      margin-left:.2rem
      padding-left:.2rem
      height:.62rem
      border-radius:.1rem
      color:#ccc
      line-height:.62rem
    .header-right
      width: 1.24rem
      float:right
      text-align:center
      .arrow-icon
        font-size:.24rem
        margin-left:-.04rem
</style>

<template>
<div class="search">
  <input type="text" placeholder="输入城市名或者拼音" class="search-input">
</div>
</template>

<script>
export default {
  name: 'CitySearch'
}
</script>
<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .search
    text-align :center
    background:$bgColor
    padding:0.1rem
    heigh:.72rem
  .search-input
    height :.62rem
    line-height :.62rem
    width:100%
    border-radius:.06rem
    text-align:center
    padding 0.1rem
    box-sizing:border-box
</style>

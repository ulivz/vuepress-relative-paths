<template>
  <div id="global-layout">
    <header>
      <div class="left">
        {{ $frontmatter.headerTitle }}
      </div>
      <div class="right">
        <a href="https://github.com/ulivz" target="_blank" class="title">ULIVZ's manuscript</a><br>
        <div class="date">Feb 17 2019</div>
      </div>
    </header>
    <component :is="layout"/>
  </div>
</template>

<script>
  export default {
    computed: {
      layout() {
        if (this.$page.path) {
          if (this.$vuepress.isLayoutExists(this.$page.frontmatter.layout)) {
            return this.$page.frontmatter.layout
          }
          return 'Layout'
        }
        return 'NotFound'
      }
    }
  }
</script>

<style lang="stylus">
header
  height 80px
  background-color #333
  text-align right
  .left
    font-size 30px
  .right
    float right
    .title, .date
      display inline-block
    .title
      font-family Arial
      font-weight 100
      margin 1rem 1.5rem 0 1.5rem
      font-size 13px
      text-transform uppercase
      color #999
      border-bottom 1px solid #aaa
    .date
      padding 0 1.5rem 1rem 1.5rem
      font-size 29px
      font-weight bold
      color #ddd
</style>

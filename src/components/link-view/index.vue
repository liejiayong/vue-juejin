<template>
  <a class="link-view-con" @click.stop :href="url" ref="nofollow noopener noreferrer" target="_blank">
    <div class="link-content">
      <div class="link-title">{{urlTitle}}</div>
      <div class="link-domain">{{linkDomain}}</div>
    </div>
    <div class="link-pic" :style="{backgroundImage: `url(${urlPic || 'https://b-gold-cdn.xitu.io/v3/static/img/defaultThumb.023ed66.svg'})`}">

    </div>
  </a>
</template>

<script>
const domainReg = /(http|https):\/\/([^\/]+)/i
export default {
  props: {
    url: String,
    urlTitle: String,
    urlPic: String
  },
  computed:{
    linkDomain() {
      let domain = this.url.match(domainReg)
      return (domain != null && domain.length>0) ? domain[2] : ''
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "../../assets/css/variable.styl"
.link-view-con
  display flex
  border-radius 8rem
  padding 20rem 30rem
  background #f9f7f7
  .link-content
    display flex
    flex-direction column
    justify-content space-between
    margin-right 20rem
    flex 1
    width 0
    font-size 30rem
    .link-title
      white-space normal
    .link-domain
      color #8a93a0
      font-size 28rem
  .link-pic
    border-radius 2px
    width 144rem
    height 144rem
    background-size cover
    background-position 50%

</style>
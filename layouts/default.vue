<template lang="pug">
.default-main-layout
  Header
    Row(justify="end", align="middle", style="height: 100%", :gutter="20")
      Col.text-right
        Dropdown(@on-click="click")
          a(href="javascript:void(0)", style="font-size: 16px; color: #515a6e")
            h3.account-select
              span.account-select-label 帳戶
              Icon(type="ios-arrow-down", size="24")
          DropdownMenu.text-left(slot="list")
            DropdownItem(name="change-pass")
              Icon.mr-1(type="md-key", size="24")
              span 更變密碼
            DropdownItem(name="login")
              Icon.mr-1(type="ios-log-out", size="24")
              span 登出
  SiderMenu
  .layout-contain
    Breadcrumb.layout-contain-breadcrumb
    Card(shadow)
      Nuxt
</template>
<script>
import Headers from "../components/Headers.vue";
import SiderMenu from "../components/SiderMenu.vue";
import Breadcrumb from "../components/Breadcrumb.vue";
export default {
  components: {
    Headers,
    SiderMenu,
    Breadcrumb,
  },
  data() {
    return {};
  },
};
</script>
<style lang="sass">
@mixin scrollHide
  overflow: scroll
  -ms-overflow-style: none
  overflow: -moz-scrollbars-none
  -webkit-overflow-scrolling: touch
  &::-webkit-scrollbar
    display: none

html
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif
  font-size: 16px
  word-spacing: 1px
  -ms-text-size-adjust: 100%
  -webkit-text-size-adjust: 100%
  -moz-osx-font-smoothing: grayscale
  -webkit-font-smoothing: antialiased
  box-sizing: border-box
  background: #f5f7f9
  +scrollHide

*,
*::before,
*::after
  box-sizing: border-box
  margin: 0

.default-main-layout
  min-height: 100%
  background: #e9e9e9
  display: flex
  flex-direction: column

.layout-contain
  margin-left: 200px
  position: relative
  padding-left: 1rem
  padding-right: 1rem
  margin-top: 30px
  min-height: 100vh

.layout-contain-breadcrumb
  font-size: 1rem
  padding: 0 1rem 1rem 1rem

.ivu-layout-footer
  background: transparent
  padding: 12px 50px
</style>

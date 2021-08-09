<template lang="pug">
Sider.layout-sider(hide-trigger :style="{ background: '#fff' }")
  .layout-sider-content
    Menu(active-name="1-2" theme="light" width="auto" :open-names="['1']")
      Submenu(name="1")
        template(slot="title")
          Icon(type="ios-navigate")
          span 首頁
        MenuItem(name="1-1") 
            nuxt-link(to="/") Home
      Submenu(name="2")
        template(slot="title")
          Icon(type="ios-keypad")
          span 會員
        MenuItem(name="2-1")
            nuxt-link(:to="{ name: 'member'}") member
</template>
<script>
export default {};
</script>
<style lang="sass">
.layout-sider
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5)
  user-select: none
  .ivu-menu-dark.ivu-menu-vertical .ivu-menu-opened
    background: #395b9f
    .ivu-menu-submenu-title
      background: #24478d

  .ivu-menu-dark.ivu-menu-vertical
    .ivu-menu-item-active:not(.ivu-menu-submenu)
      color: #fff
      background: #1877f2

.ivu-layout-sider
  position: fixed
  z-index: 12
  height: 100%
  max-width: 100%
  left: 0
  top: 0
  .layout-sider-logo
    height: 64px
    line-height: 70px
    text-align: center
    border-bottom: 1px solid rgba(255, 255, 255, 0.5)
    overflow: hidden
    .layout-sider-logo-link
      font-family: MicrosoftJhengHei
      font-size: 24px
      font-weight: bold
      font-style: normal
      font-stretch: normal
      line-height: normal
      letter-spacing: normal
      text-align: left
      color: #fffefe

    img
      height: 80%
      vertical-align: middle

  .layout-sider-content
    -ms-overflow-style: none
    overflow: -moz-scrollbars-none
    overflow-y: auto
    height: calc(100% - 60px)
    width: 100%
    position: absolute
    &::-webkit-scrollbar
      width: 0 !important
  &.i18n-enus
    .ivu-menu-vertical
      .ivu-menu-item,.ivu-menu-submenu-title
        padding-right: 30px
      .ivu-menu-item
        display: flex
      .ivu-menu-submenu-title-icon
        right: 6px
</style>

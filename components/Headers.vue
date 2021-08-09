<template lang="pug">
  Header.main-header
    Menu(mode="horizontal" theme="dark" active-name="1")
      h1.layout-logo CRUD
      .layout-nav
        MenuItem(name="1") 
          Icon(type="ios-navigate") 
          span Item1
        MenuItem(name="2")
          Icon(type="ios-keypad")  
          span Item 2
</template>

<script>
export default {};
</script>

<style lang="sass">
.main-header
  height: auto
  line-height: normal
  padding: 10px 50px
  padding-bottom: 5px
  .nuxt-link-btn
    text-align: center
    display: inline-block
    padding: 5px 16px
    border-radius: 5px
    border: solid 1px #fff
    margin-left: 5px
    min-width: 80px
</style>
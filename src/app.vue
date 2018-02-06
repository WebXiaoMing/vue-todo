<template>
  <div id="app">
      <div class="cover"></div>
      <Header></Header>
      <todo></todo>
  </div>
</template>
<script>
    import Header from './todo/header.vue'
    import Todo from './todo/todo.vue'

    export default {
       components: {
           Header,
           Todo
       }
    }
</script>
<style lang="stylus" scoped>
#app
    position relative
    top 0
    left 0
    right 0
    bottom 0
.cover
    position absolute
    top 0
    left 0
    right 0
    bottom 0
    background rgba(255,255,255,.3)
    width 100vw
    height 100vh
</style>


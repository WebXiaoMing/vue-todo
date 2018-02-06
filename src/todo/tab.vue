<template>
  <div class="tab-container">
    <span class="tab-num">{{unFinisedTodoLength}} items left</span>
    <div class="tab-status">
      <span v-for="state in filters"
            :class="{'active': state === filter}"
            @click="changeTab(state)"
      >{{state}}</span>
    </div>
    <span class="clear-completed" @click="clearCompleted">Clear completed</span>
  </div>
</template>
<script type="text/ecmascript-6">
  export default {
    props: {
      filter: {
        type: String,
        required: true
      },
      todo: {
        type: Array,
        required: true
      }
    },

    computed: {
      unFinisedTodoLength () {
        return this.todo.filter(todo => !todo.completed).length
      }
    },

    data () {
      return {
        filters: ['all', 'active', 'completed']
      }
    },

    methods: {
      changeTab (state) {
        this.$emit('clickTab', state)
      },
      
      clearCompleted (e) {
        this.$emit('clearCompleted')
      } 
    }
  }
</script>
<style lang="stylus" scoped>
  .tab-container 
    position relative
    width 100%
    height 50px
    background #fff
    top 6px
    line-height 50px
    text-align center
    color #999
    font-size 18px
  .tab-status
    display inline-block
    margin 0 150px
  .tab-status span 
    cursor pointer
    box-sizing border-box
    padding 6px 10px
  .tab-status .active
    box-sizing border-box
    border 1px solid red
  .clear-completed
    cursor pointer
</style>

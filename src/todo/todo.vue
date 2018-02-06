<template>
  <section class="add-content">
    <input 
      type="text"
      class="add-item"
      autofocus="autofocus"
      placeholder="接下来要做什么？"
      @keyup.enter="addTodo"
    />
    <item :todo="todo"
          v-for="todo in filteredTodo"
          :key="todo.id"
          @del="deleteTodo"
    />
    <tab :filter="filter"
         @clickTab="changeTab"
         :todo="todo"
         @clearCompleted="clearCompleted"
    />
  </section>
</template>

<script type="text/ecmascript-6">
  import Item from './item.vue'
  import Tab from './tab.vue'
  export default{
    data () {
      return {
        todo: [],
        id: 0,
        filter: 'all'
      }
    },

    computed: {
      filteredTodo () {
        if (this.filter === 'all') {
          return this.todo
        }
        const completed = this.filter === 'completed'
        return this.todo.filter(todo => todo.completed === completed)
      }
    },

    methods: {
      addTodo (e) {
        this.todo.unshift({
          id: this.id ++,
          content: e.target.value.trim(),
          completed: false
        })
        e.target.value = ''
      },

      deleteTodo (id) {
        this.todo.splice(this.todo.findIndex(todo => todo.id === id), 1)
      },

      changeTab (state) {
        this.filter = state
      },

      clearCompleted () {
        this.todo = this.todo.filter(todo => !todo.completed)
      }
    },
    components: {
      Item,
      Tab
    }
  }
</script>
<style lang="stylus" scoped>
.add-content
  position absolute
  left 50%
  width 800px
  margin-left -400px
  background #f9f9f9
  box-shadow 0 0 10px #aaa
  border-radius 2px
.add-content .add-item
  width 100%
  height 60px
  line-height 60px
  padding 10px 10px 10px 40px
  font-size 28px
  box-sizing border-box
  color #8e8e8e
  outline none
  border none
  border-radius 2px
</style>


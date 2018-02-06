<template>
  <section class="todo-list">
    <input 
      type="checkbox"
      class="toggle"
      v-model="todo.completed"
    />
    <span></span>
    <label class="text-content">{{todo.content}}</label>
    <button class="destory" @click="deleteTo(todo)"></button>
  </section>
</template>

<script>
  export default{
    props: {
      todo: {
        type: Object,
        required: true
      }
    },
    methods: {
      deleteTo (todo) {
        this.$emit('del', this.todo.id)
      }
    }
  }
</script>
<style lang="stylus" scoped>
.todo-list
  display inline-block
  position relative
  width 100%
  height 60px
  font-size 28px
  color #8e8e8e
  border-radius 2px
  background #fff
  margin-top 8px
  vertical-align middle
  line-height 60px
  border-bottom 1px solid rgba(0,0,0,0.06)
.toggle
  position absolute
  width 40px
  height 40px
  display inline-block
  z-index 100
  margin-left 10px
  top 50%
  margin-top -20px
  opacity 0
  cursor pointer
.toggle + span
  display inline-block
  position absolute
  width 40px
  height 40px
  background url(../img/round.svg) no-repeat
  background-size 100%
  margin-left 10px
  top 50%
  margin-top -20px
  border-radius 20px
.toggle:checked + span
  background url(../img/done.svg) no-repeat
.text-content 
  margin-left 60px
.destory
  position: absolute;
  top: 0;
  right: 10px;
  bottom: 0;
  width: 40px;
  height: 40px;
  margin: auto 0;
  font-size: 30px;
  color: #cc9a9a;
  margin-bottom: 11px;
  transition: color 0.2s ease-out;
  background-color transparent
  appearance none
  border-width 0
  cursor pointer
  outline none
.todo-list:hover{
    .destory:after{
      content: '×'
    }
  }
</style>

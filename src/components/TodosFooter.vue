<template>
  <div>
    <p class="is-pulled-left" >{{all}} items left</p></br>
    <p class="is-pulled-left" >{{active}} items left</p></br>
    <p class="is-pulled-left" >{{Completed}} items left</p></br>
    
    <visibility-input/>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import VisibilityInput from '@/components/VisibilityInput'

export default {
  components: {
    VisibilityInput
  },
  data () {
    return {
      status: 'All'
    }
  },
  computed: {
    ...mapGetters(['todos']),
    all () {
      if (this.todos) {
        return this.todos.length
      }
    },
    active () {
      if (this.todos) {
        return this.todos.filter(todo => todo.completed === false).length
      }
    },
    Completed () {
      if (this.todos) {
        return this.todos.filter(todo => todo.completed === true).length
      }
    }
  }
}
</script>

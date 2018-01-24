<template>
  <div>
    <p class="is-pulled-left">{{count}} items left</p></br>
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
    count () {
      return this.todos.filter(todo => todo.completed === false).length
    }
  }
}
</script>

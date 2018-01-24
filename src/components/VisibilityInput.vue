<template>
  <div>
    <b-field class="is-pulled-right">
      <b-radio-button v-model="visibility"
        native-value="all">
        <span>All</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="active">
        <span>Active</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="completed">
        <span>Completed</span>
      </b-radio-button>
      <b-radio-button v-model="visibility"
        native-value="ClearCompleted" >
        <span>Clear Completed</span>
      </b-radio-button>
    </b-field>
  </div>
</template>

<script>
import { store } from '@/store'

export default {
  computed: {
    all () {
      if (this.todos) {
        return this.todos.length
      } else {
        return 0
      }
    },
    active () {
      if (this.todos) {
        return this.todos.filter(todo => todo.completed === false).length
      } else {
        return 0
      }
    },
    Completed () {
      if (this.todos) {
        return this.todos.filter(todo => todo.completed === true).length
      } else {
        return 0
      }
    },
    visibility: {
      get: function () {
        return store.state.visibility
      },
      set: function (newValue) {
        store.dispatch('changeVisibility', newValue)
      }
    }
  }
}
</script>

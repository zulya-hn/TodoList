<template>
  <div>
    <AddTodo
      @add-todo="addTodo($event, day)"
      class="my-4"
      :dayName="dayName"
      @removeAllTodos="removeAllTodos()"
    />

    <draggable
      v-model="days"
      group="list"
      @start="drag = true"
      @end="drag = false"
      @change="changeElementPosition($event, dayName)"
    >
      <li class="vertical-center" v-for="todo of days" :key="todo.id">
        <span>
          <label
            :for="todo.id + todo.title"
            :class="{ done: todo.completed }"
            @click="changeTodoState(todo)"
          >
            {{ todo.title }}
          </label>
        </span>

        <button @click="removeTodo(todo.id, day)" class="btn-reset close-red">
          <img src="close-boot.svg" width="20" height="20" aria-hidden="true" />
        </button>
      </li>
    </draggable>
  </div>
</template>

<script>
import Draggable from 'vuedraggable'
import AddTodo from './AddTodo'

export default {
  components: {
    Draggable,
    AddTodo
  },
  props: {
    dayName: String
  },
  data() {
    return {
      day: {
        items: []
      }
    }
  },
  mounted() {
    this.getTodosFromStorage()
  },
  computed: {
    days: {
      get() {
        return this.day.items.slice().sort((a, b) => a.completed > b.completed)
      },
      set(value) {
        this.day.items = value
      }
    }
  },
  methods: {
    changeElementPosition(event, day) {
      if (event.added !== undefined) {
        event.added.element.day = day
        const element = event.added.element
        const parsedChange = JSON.stringify(element)
        localStorage.setItem(element.id, parsedChange)
      }
    },
    removeTodo(id, arr) {
      arr.items = arr.items.filter(t => t.id !== id)
      localStorage.removeItem(id)
    },
    removeAllTodos() {
      this.days.forEach(element => {
        localStorage.removeItem(element.id)
      })
      this.days = []
    },
    addTodo(todo, arr) {
      console.log(todo)
      arr.items.push(todo)
      const parsed = JSON.stringify(todo)
      localStorage.setItem(todo.id, parsed)
    },
    getTodosFromStorage() {
      const keys = Object.keys(localStorage)

      for (const key of keys) {
        localStorage.getItem(key)
        const todoFromStorage = localStorage.getItem(key)

        try {
          const parsedFromStorage = JSON.parse(todoFromStorage)
          const dayFromStorage = parsedFromStorage.day

          if (dayFromStorage === this.dayName) {
            this.day.items.push(parsedFromStorage)
          }
        } catch (error) {}
      }
    },
    changeTodoState(todo) {
      todo.completed = !todo.completed
      const parsed = JSON.stringify(todo)
      localStorage.setItem(todo.id, parsed)
    }
  }
}
</script>


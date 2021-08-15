<template>
  <main class="main-tag" :class="theme == 'light' ? '' : 'dark-theme'">
    <div class="container">
      <div class="row">
        <div class="task-card col text-center position-relative">
          <h2>Saturday</h2>
          <button type="button" class="btn-reset light" @click="toggleStyles()">
            <img
              alt="bulb"
              class="bulb"
              :src="
                theme == 'light' ? 'bi-lightbulb-fill.svg' : 'bi-lightbulb.svg'
              "
            />
          </button>
          <TodoItem :dayName="'sat'" />
        </div>
        <div class="task-card col text-center">
          <h2>Sunday</h2>
          <TodoItem :dayName="'sun'" />
        </div>
      </div>

      <div class="row text-center">
        <div class="task-card col">
          <h2 class="">Other days</h2>
          <TodoItem :dayName="'other'" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import TodoItem from './TodoItem'
export default {
  data() {
    return {
      theme: null
    }
  },
  components: {
    TodoItem
  },
  methods: {
    toggleStyles() {
      this.theme = this.theme == 'light' ? 'dark' : 'light'
    },
    setThemeOnLoad() {
      let time = new Date().getHours()
      time > 6 && time < 21 ? (this.theme = 'light') : (this.theme = 'dark')
    }
  },
  mounted() {
    this.setThemeOnLoad()
  }
}
</script>

<style lang="scss">
.main-tag {
  h2 {
    color: #465046;
  }
  background-color: #e6f9e7;
  min-height: 100vh;
  .btn-reset {
    background: transparent;
    border: none;
    outline: none;
  }
  .createbtn {
    border: 2px solid #465046;
    border-radius: 0.5rem;
    background-color: #cdefce;
  }
  .createinput {
    border: 2px solid #465046;
    border-radius: 0.5rem;
    background-color: #f6fff7;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  &.dark-theme {
    h2 {
      color: #b1b6bb;
    }
    background-color: #2b3d50;
    color: #b1b6bb;
    button {
      color: #b1b6bb;
    }
    .createbtn {
      background-color: #1d274a;
      border-color: #060b1d;
      border-radius: 0.5rem;
      color: #ced0d3;
    }
    .createinput {
      background-color: #000f466b;
      border-color: #060b1d;
      border-radius: 0.5rem;
      color: #ced0d3;
    }
    li {
      border: 1px solid #060b1d;
      color: #ced0d3;
    }
    .task-card {
      border: 2px #060b1d solid;
      background-color: #2b3d50;
    }
  }

  button,
  input {
    outline: none;
  }

  .close-red {
    button {
      color: #eb0f0f;
      fill: #eb0f0f;
    }
  }

  .task-card {
    border: 2px #dee2e6 solid;
    padding: 1rem 0.5rem;
    background-color: #e6f9e7;
  }

  .light {
    position: absolute;
    top: 1.5rem;
    right: 1rem;
  }

  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  label {
    margin-bottom: 0;
  }

  li {
    border: 1px solid #617161;
    display: flex;
    justify-content: space-between;
    padding-right: 0.5rem;
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
    padding-left: 1rem;
    margin-bottom: 0.5rem;
    align-items: center;
    border-radius: 1rem;
  }

  input {
    margin-right: 0.2rem;
  }

  .done {
    text-decoration: line-through;
  }
}
</style>

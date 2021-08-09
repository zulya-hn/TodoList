<template>
  <main class="main-tag">
    <div class="container">
      <div class="row">
        <div class="task-card border-right-0 col text-center position-relative">
          <h2>Saturday</h2>
          <button type="button" class="btn-reset light" @click="toggleStyles()">
            <!-- <img src="bi-lightbulb.svg" alt="" />
            <img src="bi-lightbulb-fill.svg" alt="" /> -->
            <img alt="bulb" class="bulb" :src="'1'" @click="closestBtn()" />
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
  components: {
    TodoItem
  },
  methods: {
    toggleStyles() {
      let mainTag = document.querySelector('.main-tag')
      mainTag.classList.toggle('dark-theme')
    },
    closestBtn() {
      let mainTag = document
        .querySelector('.main-tag')
        .classList.contains('dark-theme')

      console.log('привет')
    }
  }
  // created: function () {
  //   closestBtn()
  // }
  // computed: {
  //   closestBtn() {
  //     return document
  //       .querySelector('.bulb')
  //       .closest('.light')
  //       .classList.contains('dark-theme')
  //       ? 'bi-lightbulb.svg'
  //       : 'bi-lightbulb-fill.svg'
  //   }
  // }
}
</script>

<style lang="scss">
.main-tag {
  .btn-reset {
    background: transparent;
    border: none;
    outline: none;
  }
  &.dark-theme {
    background: #2b3d50;
    color: #b1b6bb;
    button {
      color: #b1b6bb;
    }
    .createbtn {
      background-color: #1d274a;
      border: 2px solid #060b1d;
      border-radius: 0.5rem;
      color: #ced0d3;
    }
    .createinput {
      background-color: #000f466b;
      border: 2px solid #060b1d;
      border-radius: 0.5rem;
      color: #ced0d3;
      padding-left: 0.5rem;
      padding-right: 0.5rem;
    }
    li {
      border: 1px solid #060b1d;
      border-radius: 1rem;
      color: #ced0d3;
    }
    .task-card {
      border: 2px #060b1d solid;
    }
  }

  button,
  input {
    outline: none;
  }

  .task-card {
    border: 2px #dee2e6 solid;
    padding: 1rem 0.5rem;
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
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding-right: 0.5rem;
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
    padding-left: 1rem;
    margin-bottom: 0.5rem;
    align-items: center;
  }

  input {
    margin-right: 1rem;
  }

  .done {
    text-decoration: line-through;
  }
}
</style>

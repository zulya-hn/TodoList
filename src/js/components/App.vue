<template>
  <main class="main-tag">
    <div class="container">
      <div class="row">
        <div class="task-card col text-center position-relative">
          <h2>Saturday</h2>
          <button type="button" class="btn-reset light" @click="toggleStyles()">
            <!-- <img alt="bulb" class="bulb" :src="BulbIcon()" /> -->
            <!-- <img alt="bulb" class="bulb" src="bi-lightbulb-fill.svg" /> -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-lightbulb-fill"
              viewBox="0 0 16 16"
            >
              <path
                d="M2 6a6 6 0 1 1 10.174 4.31c-.203.196-.359.4-.453.619l-.762 1.769A.5.5 0 0 1 10.5 13h-5a.5.5 0 0 1-.46-.302l-.761-1.77a1.964 1.964 0 0 0-.453-.618A5.984 5.984 0 0 1 2 6zm3 8.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1l-.224.447a1 1 0 0 1-.894.553H6.618a1 1 0 0 1-.894-.553L5.5 15a.5.5 0 0 1-.5-.5z"
              />
            </svg>
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
    }
    // BulbIcon() {
    //   let mainTag = document
    //     .querySelector('.main-tag')
    //     .classList.contains('dark-theme')
    //   mainTag ? 'bi-lightbulb.svg' : 'bi-lightbulb-fill.svg'

    //   console.log(mainTag)
    // }
  }
  // computed: {}
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

  .close-red {
    button {
      color: #eb0f0f;
      fill: #eb0f0f;
    }
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
    margin-right: 0.2rem;
  }

  .done {
    text-decoration: line-through;
  }
}
</style>

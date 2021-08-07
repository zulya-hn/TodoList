<template>
  <main>
    <div class="container">
      <div class="row my-lg-40">
        <div class="task-card border-right-0 col">
          <h2 class="mt-2 text-center">Saturday</h2>
          <TodoItem :dayName="'sat'" />
        </div>
        <div class="task-card col">
          <h2 class="mt-2 text-center">Sunday</h2>
          <TodoItem :dayName="'sun'" />
        </div>
      </div>

      <div class="row text-center">
        <div class="task-card col">
          <h2 class="mt-2 text-center">Other days</h2>
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
  }
}
</script>

<style lang="scss">
.task-card {
  border: 2px #dee2e6 solid;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
  align-items: center;
}

.rm {
  background: #da1f24;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}

input {
  margin-right: 1rem;
}

.done {
  text-decoration: line-through;
}
</style>

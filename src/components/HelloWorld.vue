<template>
  <div class="hello">
    <form>
      <button @click="addTodo()">add task</button>
      <button @click="deleteTodo()">delete task</button>
      <p>input: 
        <input
          v-model="newTodo"
          type="text"
        >
      </p>
      <p>task: {{ newTodo }}</p>
    </form>
    <div class="task-list">
      <label
        v-for="(todo, index) in todos"
        :key="index"
        class="task-list__item"
      >
        <input
          v-model="todo.done"
          type="checkbox"
        >
        {{ todo.text }}
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      todos: [
        { text: 'vue-router', done: false},
        { text: 'vuex', done: false},
        { text: 'vue-loader', done: false},
        { text: 'awesome-vue', done: true},
      ],
      newTodo: '',
    }
  },
  methods: {
    addTodo: function() {
      const text = this.newTodo && this.newTodo.trim()
      if (!text) return

      this.todos.push({
        text: text,
        done: false,
      })
      this.newTodo = ''
    },
    deleteTodo: function() {
      this.todos = this.todos.filter(todos => !todos.done)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.task-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.task-list__item {
  width: 270px;
  text-align: left;
}
.task-list__item--checked {
  width: 270px;
  text-align: left;
  color: #85a6c6;
}
</style>

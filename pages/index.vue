<template>
  <div>
    <form v-on:submit.prevent>
      <input type="text" v-model="newItem" />
      <button v-on:click="addItem">
        追加
      </button>
    </form>
    <ul>
      <li v-for="(todo, index) in todos" :key="todo.id">
        <input type="checkbox" v-model="todo.isDone" />
        <span v-bind:class="{ done: todo.isDone }">
          {{ todo.item }}
        </span>
        <button v-on:click="deleteItem(index)">
          削除
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: "",
      todos: []
    }
  },
methods: {
  addItem: function() {
    if(this.newItem === "") { return }
    let todo = {
      item: this.newItem,
      isDone: false
    }
    this.todos.push(todo)
    this.newItem = ""
  },
  deleteItem: function(index) {
    this.todos.splice(index, 1)
  }
}
}
</script>

<style scoped>
ul {
  list-style: none;
}

.done {
  text-decoration: line-through;
}
</style>
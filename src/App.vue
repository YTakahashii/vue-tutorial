<template>
  <div id="app">
    <h1>Lovely Vue</h1>
    <input type="text" v-model="message">
    <button :disabled="isDisabled" @click="add">追加</button>
    <!-- `@`は `v-on`の省略 -->
    <!-- `:` を前に付けると右辺はスクリプトとして変数が展開される (v-bindの省略) -->
    {{message}}
    <br>
    <template v-if="todos.length === 0">タスクはありません。</template>
    <template v-else>
      <ul>
        <!-- <li v-for="todo in todos" :key="todo.id">{{todo.text}}</li> -->
        <TaskCard
          v-for="todo in todos"
          :key="todo.id"
          :text="todo.text"
          :id="todo.id"
          @remove-task="remove"
        />
      </ul>
    </template>
  </div>
</template>

<script>
import TaskCard from "./components/TaskCard";

export default {
  name: "App",
  components: {
    TaskCard
  },
  data: () => ({
    message: "message",
    todos: [{ id: 1, text: "Todo1" }]
  }),
  methods: {
    add() {
      const newTodo = {
        id: this.todos.length + 1,
        text: this.message
      };
      this.todos.push(newTodo);
      this.message = "";
    },
    remove(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
  // 算出プロパティ
  computed: {
    isDisabled() {
      return this.message.length === 0;
    }
  }
};
</script>

<style></style>
<template>
  <div id="app">
    <h1>Lovely Vue</h1>
    <input type="text" v-model="message">
    <button :disabled="isDisabled" @click="add">追加</button>
    <!-- `@`は `v-on`の省略 -->
    <!-- `:` を前に付けると右辺はスクリプトとして変数が展開される (v-bindの省略) -->
    <br>
    <ul>
      <li v-for="todo in todos" :key="todo.id" class="task-card">{{todo.text}}</li>
    </ul>
    {{message}}
  </div>
</template>

<script>
export default {
  name: "App",
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
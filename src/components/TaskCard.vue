<template>
  <li class="task-card">
    <span>{{text}}</span>
    <button @click="remove">削除</button>
  </li>
</template>

<script>
export default {
  name: "TaskCard",
  props: {
    id: {
      type: Number,
      required: true
    },
    text: {
      type: String,
      default: ""
    }
  },
  methods: {
    remove() {
      console.log(`remove ${this.id}`);
      this.$emit("remove-task", this.id); // <TaskCard />のpropsに@remove-task="remove"
    }
  }
};
</script>

<style>
.task-card {
  border: solid 1px;
  margin: 5px;
  padding: 2px;
  width: 250px;
}
.task-card > button {
  float: right;
}
</style>

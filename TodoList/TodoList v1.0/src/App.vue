<template>
  <div id="container">
    <TodoInput :todoList="todoList" :getTodo="getTodo"></TodoInput>
    <TodoList
      :todoList="todoList"
      :getCheckInfo="getCheckInfo"
      :deleteById="deleteById"
    ></TodoList>
    <TodoTotal
      :todoList="todoList"
      :changeCheckedInfoAll="changeCheckedInfoAll"
      :deleteCheckedAll="deleteCheckedAll"
    ></TodoTotal>
  </div>
</template>

<script>
import { nanoid } from "nanoid";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoTotal from "./components/TodoTotal.vue";
export default {
  components: {
    TodoInput,
    TodoList,
    TodoTotal,
  },
  data() {
    return {
      todoList: [
        { id: "001", todoName: "吃饭", isChecked: true },
        { id: "002", todoName: "睡觉", isChecked: false },
        { id: "003", todoName: "打豆豆", isChecked: true },
      ],
    };
  },
  methods: {
    getTodo(value) {
      const todo = { id: nanoid(), todoName: value, isChecked: false };
      this.todoList.unshift(todo);
    },
    getCheckInfo(id) {
      this.todoList.forEach((item) => {
        if (item.id === id) item.isChecked = !item.isChecked;
      });
    },
    deleteById(id) {
      this.todoList = this.todoList.filter((item) => {
        return item.id !== id;
      });
    },
    changeCheckedInfoAll(value) {
      this.todoList.forEach((item) => {
        if (item.isChecked !== value) {
          item.isChecked = value;
        }
      });
    },
    deleteCheckedAll() {
      this.todoList = this.todoList.filter((item) => {
        return item.isChecked === false;
      });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#container {
  width: 700px;
  margin: 50px auto;
  border-style: solid;
  border-color: #e2e2e2;
  border-radius: 5px;
}
</style>

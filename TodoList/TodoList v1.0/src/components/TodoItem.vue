<template>
  <div class="TodoList">
    <li v-for="todo in todoList" :key="todo.id">
      <input
        type="checkbox"
        class="todoCheckBox"
        :checked="todo.isChecked"
        @click="changeListCheckInfo(todo.id)"
      />{{ todo.todoName }}<button @click="deleteTodo(todo.id)">删除</button>
    </li>
  </div>
</template>

<script>
export default {
  props: ["todoList", "getCheckInfo", "deleteById"],
  methods: {
    changeListCheckInfo(id) {
      this.getCheckInfo(id);
    },
    deleteTodo(id) {
      this.deleteById(id);
    },
  },
};
</script>

<style scoped>
.TodoList {
  list-style: none;
  border: 2px solid #ccc;
  border-radius: 5px;
}

.TodoList > li {
  position: relative;
  height: 35px;
  border-bottom: 2px solid #ccc;
  line-height: 35px;
  padding-left: 15px;
  vertical-align: middle;
}

.TodoList > li:last-child {
  border-bottom: none;
}

.TodoList > li:hover {
  background-color: #f0f0f0;
}

.TodoList button {
  display: none;
  position: absolute;
  width: 60px;
  height: 25px;
  background-color: #de4c24;
  right: 15px;
  top: 5px;
  border: 1px solid #de4c24;
  border-radius: 3px;
  color: white;
}

.TodoList button:hover {
  background-color: #e66b49;
  border-color: #e66b49;
}

.TodoList > li:hover button {
  display: inline-block;
}

.TodoList > li > .todoCheckBox {
  margin-right: 5px;
}

/* 设置复选框样式 */
.todoCheckBox {
  appearance: none; /* 隐藏默认的复选框样式 */
  width: 15px; /* 设置复选框的宽度 */
  height: 15px; /* 设置复选框的高度 */
  border: 2px solid #b6b4b4; /* 设置复选框的边框 */
  border-radius: 50%; /* 设置复选框为圆形 */
  position: relative; /* 设置为相对定位，以便伪元素定位 */
  cursor: pointer; /* 设置鼠标样式为手型 */
}

.todoCheckBox::before {
  content: ""; /* 伪元素内容为空 */
  display: block; /* 设置为块级元素 */
  width: 100%; /* 设置宽度为100% */
  height: 100%; /* 设置高度为100% */
  border-radius: 50%; /* 设置为圆形 */
  background-color: #ffffff; /* 设置背景颜色为白色 */
}

.todoCheckBox:checked::after {
  content: ""; /* 伪元素内容为空 */
  display: block; /* 设置为块级元素 */
  width: 50%; /* 设置宽度为50% */
  height: 50%; /* 设置高度为50% */
  border-radius: 50%; /* 设置为圆形 */
  background-color: rgb(9, 185, 9); /* 设置背景颜色为绿色 */
  position: absolute; /* 设置为绝对定位 */
  top: 25%; /* 设置顶部位置 */
  left: 25%; /* 设置左侧位置 */
}
</style>

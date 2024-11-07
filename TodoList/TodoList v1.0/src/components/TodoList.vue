<template>
  <div id="list-container">
    <ul class="TodoList">
      <TodoItem
        :todoList="todoList"
        :getCheckInfo="getCheckInfo"
        :deleteById="deleteById"
      ></TodoItem> 
    </ul>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  components: { TodoItem },
  props: ["todoList", "getCheckInfo", "deleteById"],
};
</script>

<style scoped>
#list-container {
  margin: 10px;
}
</style>

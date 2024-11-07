<template>
  <div id="input-container">
    <input
      class="addTodo"
      type="text"
      placeholder="请输入你的任务名称，按回车确认"
      v-model="todoInput"
      @keyup.enter="getTodoInput"
    />
  </div>
</template>

<script>
export default {
  props: ["getTodo"],
  data() {
    return {
      todoInput: "",
    };
  },
  methods: {
    getTodoInput() {
      this.getTodo(this.todoInput);
      this.todoInput = "";
    },
  },
};
</script>

<style scoped>
#input-container {
  height: 60px;
}

.addTodo {
  width: 660px;
  height: 40px;
  margin: 10px 10px;
  padding-left: 20px;
  border: 2px solid #ccc;
  border-radius: 5px;
}

.addTodo::placeholder {
  /* text-indent: 1em; */
  vertical-align: middle;
}

.addTodo:hover,
.addTodo:focus {
  background-color: #f0f0f0;
  border-color: #828181;
}
</style>

<template>
  <div id="total-container">
    <input
      type="checkbox"
      name="checkedAll"
      class="checkedAll"
      v-model="isCheckedAll"
      @change="changeAll"
    />
    <span class="totalInfo">已完成{{ todoDone }} / 全部{{ todoTotal }}</span>
    <button class="clearChecked" @click="clearAllDone">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isCheckedAll: false,
    };
  },
  props: ["todoList", "changeCheckedInfoAll", "deleteCheckedAll"],
  computed: {
    todoDone() {
      return this.todoList.filter((item) => {
        return item.isChecked === true;
      }).length;
    },
    todoTotal() {
      return this.todoList.length;
    },
  },
  methods: {
    changeAll() {
      this.changeCheckedInfoAll(this.isCheckedAll);
    },
    clearAllDone() {
      this.deleteCheckedAll();
    },
  },
};
</script>

<style scoped>
#total-container {
  height: 30px;
  text-align: center;
  line-height: 30px;
  margin-bottom: 10px;
}

.checkedAll {
  margin-right: 20px;
}

.totalInfo {
  margin-right: 380px;
}

.clearChecked {
  width: 120px;
  height: 30px;
  background-color: #de4c24;
  color: white;
  border: 1px solid #de4c24;
  border-radius: 5px;
}

.clearChecked:hover {
  background-color: #e66b49;
  border-color: #e66b49;
}
</style>

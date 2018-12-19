<template>
  <div id="app">
    <div>
      <input type="text" v-model="inputValue" @keyup.enter="handleSubmit">
      <input type="submit" @click="handleSubmit">
    </div>
    <ul>
      <todoItem
        v-for="(item,index) of list"
        :key="index"
        :content="item"
        :index="index"
        @delete="handleDelete"
      ></todoItem>
    </ul>
  </div>
</template>

<script>
import todoItem from "./components/todoItem.vue";

export default {
  components: { todoItem: todoItem },
  data() {
    return {
      inputValue: "",
      list: []
    };
  },
  methods: {
    handleSubmit() {
      if (this.inputValue) {
        this.list.unshift(this.inputValue);
        this.inputValue = "";
      }
    },
    handleDelete(index) {
      this.list.splice(index, 1);
    }
  }
};
</script>

<style scoped>
</style>

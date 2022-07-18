<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" />
    <label for="toggle-all"></label>
    <!-- label 可以关联一个表单标签 -->
    <input
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      @keyup.enter="enterFn()"
      v-model="task"
      autofocus
    />
  </header>
</template>

<script>
export default {
  data() {
    return {
      task: "",
    };
  },
  methods: {
    enterFn() {
      //   console.log(this.task);
      if (!this.task.trim()) {
        this.task = "";
        return alert("请输入任务");
      }
      this.$emit("addTask", this.task);
      this.task = "";
    },
  },
};
</script>
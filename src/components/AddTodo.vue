<template>
  <div class="submit-form">
    <div v-if="!submitted">
      <div class="form-group">
        <label for="title">任务</label>
        <input
          type="text"
          class="form-control"
          id="title"
          required
          v-model="todo.title"
          name="title"
        />
      </div>

      <div class="form-group">
        <label for="description">详情</label>
        <input
          class="form-control"
          id="todo"
          required
          v-model="todo.description"
          name="description"
        />
      </div>

      <button @click="saveTodo" class="btn btn-success">提交</button>
    </div>

    <div v-else>
      <h4>提交成功</h4>
      <button class="btn btn-success" @click="newTodo">添加</button>
    </div>
  </div>
</template>

<script>
import TodoDataService from "../services/TodoDataService";

export default {
  name: "add-todo",
  data() {
    return {
      // tutorial: {
      //   id: null,
      //   title: "",
      //   description: "",
      //   done: false
      // },
      todo: {
        // id: null,
        title: "",
        description: "",
        done: false,
      },
      submitted: false,
    };
  },
  methods: {
    saveTodo() {
      var data = {
        title: this.todo.title,
        description: this.todo.description,
        status: this.todo.done,
      };
      alert(data);
      TodoDataService.create(data)
        .then((response) => {
          this.todo.id = response.data.id;
          console.log(response.data);
          this.submitted = true;
        })
        .catch((e) => {
          console.log(e);
        });

      // alert(123)
    },

    newTodo() {
      this.$nextTick(() => {
        this.submitted = false;
        this.todo = {};
      });
    },
  },
};
</script>

<style>
.submit-form {
  max-width: 300px;
  margin: auto;
}
</style>

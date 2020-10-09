<template>
  <div class="form">
    <form v-on:submit.prevent="submitTodo">
      <input
        type="text"
        placeholder="Enter a task..."
        class="form__input"
        v-model="todo"
      />
      <button class="form__button" type="submit">Add task</button>
    </form>
  </div>
</template>

<script>
export default {
  inject: ["global"],
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    submitTodo() {
      // this.$emit("addTodo", this.todo);
      this.global.addTodo(this.todo);
      this.todo = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  margin-bottom: 50px;

  form {
    width: 100%;
  }

  &__input {
    height: 35px;
    width: 350px;
    max-width: 100%;
    margin-right: 10px;
    border-radius: 3px;
    padding: 0 10px;
    background-color: white;
    font-size: inherit;
  }

  &__button {
    background-color: #61dbfb;
    color: #394049;
    border-radius: 3px;
    padding: 10px 15px;
  }

  @media (max-width: 700px) {
    display: flex;

    &__input,
    &__button {
      width: 100%;
    }

    &__input {
      margin-bottom: 15px;
    }
  }
}
</style>
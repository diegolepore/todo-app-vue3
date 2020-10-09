<template>
  <div class="todo-main">
    <Header />
    <Form />
    <TodoList />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Form from "@/components/Form";
import TodoList from "@/components/TodoList";
import global from "@/global.js";

export default {
  provide: {
    global,
  },
  components: {
    Header,
    Form,
    TodoList,
  },
};
</script>

<style lang="scss">
* {
  font-family: "Montserrat", sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  list-style: none;
  text-decoration: none;
  border: 0;
  background: transparent;
}

body {
  background-color: #fed330;
  height: 100vh;
  font-size: 16px;
}

.todo-main {
  width: 900px;
  max-width: 90%;
  background-color: #394049;
  margin: 40px auto;
  padding: 50px;
  color: #d3d4d6;
  border-radius: 5px;

  @media (max-width: 768px) {
    margin-top: 20px;
    padding: 30px;
  }
}
</style>
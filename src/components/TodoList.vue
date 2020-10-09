<template>
  <div class="todos">
    <ul class="todos__list">
      <li
        v-for="(task, index) of global.state.tasksFiltered"
        :key="index"
        :class="{ 'todos__item--finished': task.done }"
        class="todos__item"
      >
        <div class="todos__title-and-btn">
          <button
            @click="global.toggleTaskStatus(task)"
            class="todos__check-btn"
          >
            <font-awesome-icon icon="check-circle" />
          </button>

          <p class="todos__text">{{ task.description }}</p>
        </div>
        <button @click="global.deleteTask(task)" class="todos__delete-btn">
          <font-awesome-icon icon="trash-alt" />
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  inject: ["global"],
  mounted() {
    this.global.filterTodos("all");
  },
};
</script>

<style lang="scss" scoped>
.todos {
  $parent: &;

  &__list {
    border-top: 1px solid #7e8187;
  }

  &__item {
    display: flex;
    justify-content: space-between;
    padding: 15px 0;
    border-bottom: 1px solid #7e8187;

    &--finished {
      #{ $parent } {
        &__check-btn {
          color: #20bf6b;
        }

        &__text {
          text-decoration: line-through;
        }
      }
    }
  }

  &__title-and-btn {
    display: flex;
  }

  &__check-btn,
  &__delete-btn {
    color: #7e8187;
    outline: none;
    cursor: pointer;
  }

  // &__check-btn {
  // }

  // &__delete-btn {
  // }

  &__text {
    margin-left: 15px;
  }
}
</style>
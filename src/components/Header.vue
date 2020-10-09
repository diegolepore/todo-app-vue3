<template>
  <div>
    <header class="header">
      <div class="header__date">
        <h1 class="header__date-date">{{ dateNow }}</h1>
        <h3 class="header__date-active">{{ activeTasks() }}</h3>
      </div>

      <nav class="header__nav">
        <ul class="header__nav-list">
          <li
            @click="global.filterTodos"
            class="header__nav-item"
            :class="{
              'header__nav-item--active': global.state.activeTab === 'all',
            }"
          >
            All Tasks
          </li>
          <li
            @click="global.filterTodos('undone')"
            class="header__nav-item"
            :class="{
              'header__nav-item--active': global.state.activeTab === 'undone',
            }"
          >
            Incomplete Tasks
          </li>
          <li
            @click="global.filterTodos('done')"
            class="header__nav-item"
            :class="{
              'header__nav-item--active': global.state.activeTab === 'done',
            }"
          >
            Complete Tasks
          </li>
        </ul>
      </nav>
    </header>
  </div>
</template>

<script>
export default {
  inject: ["global"],
  setup() {
    return {};
  },
  methods: {
    activeTasks() {
      const activeTasks = this.global.state.tasks.filter((task) => !task.done);
      const activeLength = activeTasks.length;
      const taskPluralSingular =
        activeLength > 1 || activeLength < 1 ? "tasks" : "task";
      return `${activeLength} active ${taskPluralSingular}`;
    },
  },
  computed: {
    dateNow() {
      const d = new Date();
      return `${d.getDate()} / ${d.getMonth() + 1} / ${d.getFullYear()}`;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
  flex-wrap: wrap;

  @media (max-width: 700px) {
    flex-direction: column;
  }

  &__date {
    &-date {
      font-size: 20px;
      margin-bottom: 5px;
    }
    &-active {
      font-size: 13px;
      color: #61dbfb;
    }

    @media (max-width: 768px) {
      &-active {
        margin-bottom: 15px;
      }
    }
  }

  &__nav {
    &-list {
      display: flex;
    }

    &-item {
      margin: 0 15px;
      color: #7e8187;
      cursor: pointer;

      &--active {
        color: #d3d4d6;
      }
    }

    @media (max-width: 768px) {
      &-item {
        margin-left: 0;
      }
    }

    @media (max-width: 700px) {
      &-list {
        flex-direction: column;
      }

      &-item {
        margin-bottom: 12px;
      }
    }
  }
}
</style>
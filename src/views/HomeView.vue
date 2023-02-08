<template>
  <div>
    <div class="top-area">
      <p class="top-title">TOP (予定一覧表示)</p>
    </div>
    <div class="main-area">
      <filter-list :filterStatus="filterStatus"></filter-list>
      <div class="flex justify-center">
        <ul class="todo-list">
          <li class="flex justify-end">
            <button class="add-button" @click="$router.push('/add')">
              新規登録
            </button>
          </li>
          <li v-if="!todoList.length">登録されている予定はありません。</li>
          <li v-for="todo in todoList" :key="todo.id">
            <todo-list :todo="todo"></todo-list>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import FilterList from "@/components/FilterList.vue";
import TodoList from "@/components/TodoList.vue";
import { defineComponent, ref } from "@vue/composition-api";
import { Todo } from "@/interface/todo";

export default defineComponent({
  components: { TodoList, FilterList },
  setup() {
    /**
     * ローカルストレージのデータを取得・保持
     */
    const dataList: Todo[] = JSON.parse(
      window.localStorage.getItem("todoList") ?? ""
    );

    const filterStatus = ref("3");

    const todoList = ref<Todo[]>(
      dataList.sort(function (a, b) {
        if (a.status > b.status) return 1;
        if (a.status < b.status) return -1;

        if (a.endDate > b.endDate) return 1;
        if (a.endDate < b.endDate) return -1;
        return 0;
      })
    );

    /**
     * ステータスの更新処理
     *
     * @param {number} id
     * @param {number} status
     */

    /**
     * フィルターの更新処理
     *
     * @param {string} status
     */

    return {
      filterStatus,
      todoList,
    };
  },
});
</script>
<style lang="postcss" scoped>
.top-area {
  @apply flex justify-center items-center my-7;
}
.top-title {
  @apply my-5 text-2xl font-semibold;
}
.add-button {
  transition: all ease 0.2s;
  @apply border border-solid font-medium py-2 px-3 rounded mx-2;
}
.add-button:hover {
  transition: all ease 0.2s;
  @apply bg-gray-500 text-white;
}
.detail-area .change-progress-area {
  @apply w-1/5;
}
.todo-list li {
  @apply border-b border-solid py-4 w-[700px];
}
.todo-list li:last-child {
  @apply border-none;
}
</style>

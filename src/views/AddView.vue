<template>
  <div>
    <div class="top-area">
      <p class="top-title">新規登録</p>
    </div>
    <div class="main-area">
      <div class="my-5">
        <input
          class="w-[500px]"
          placeholder="タイトル"
          type="text"
          v-model="title"
        />
      </div>
      <div class="my-5">
        <textarea
          class="w-[500px]"
          placeholder="内容"
          name=""
          id=""
          cols="30"
          rows="10"
          v-model="description"
        ></textarea>
      </div>
      <div class="flex justify-between my-5">
        <input class="w-[230px]" type="date" v-model="startDate" />
        <p>~</p>
        <input class="w-[230px]" type="date" v-model="endDate" />
      </div>

      <button class="add-button" @click="addTodo()">登録</button>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "@vue/composition-api";
import { useRouter } from "@/router/use-router";
import { Todo } from "@/interface/todo";

export default defineComponent({
  setup() {
    const router = useRouter();

    const title = ref("");
    const description = ref("");
    const startDate = ref("");
    const endDate = ref("");

    /**
     * 新規登録
     */
    const addTodo = () => {
      let dataList: Todo[] = JSON.parse(
        window.localStorage.getItem("todoList") ?? ""
      );
      const id: number = dataList.length
        ? dataList.reduce((a: Todo, b: Todo) => (a.id > b.id ? a : b)).id + 1
        : 1;
      const dataset: Todo = {
        id: id,
        status: 0,
        title: "title",
        description: "description",
        startDate: "2022/12/12",
        endDate: "2022/12/30",
      };
      dataList.push(dataset);
      window.localStorage.setItem("todoList", JSON.stringify(dataList));
      router.push("/");
    };

    return {
      title,
      description,
      startDate,
      endDate,
      addTodo,
    };
  },
});
</script>
<style lang="postcss" scoped>
.top-area {
  @apply flex justify-center items-center my-7;
}
.main-area {
  @apply w-[500px] mx-auto;
}
.top-title {
  @apply my-5 text-2xl font-semibold;
}
input {
  @apply px-3 py-2 border border-solid border-gray-300 rounded outline-none;
}
textarea {
  @apply px-3 py-2 border border-solid border-gray-300 rounded outline-none resize-none;
}
.add-button {
  transition: all ease 0.2s;
  @apply bg-blue-700 text-white font-semibold py-2 px-3 rounded mx-2 w-[100px];
}
</style>

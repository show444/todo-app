<template>
  <div>
    <div class="top-area">
      <p class="top-title">予定詳細</p>
    </div>
    <div class="main-area">
      <div class="my-5">
        <input class="w-[500px]" placeholder="タイトル" type="text" />
      </div>
      <div class="my-5">
        <textarea
          class="w-[500px]"
          placeholder="内容"
          name=""
          id=""
          cols="30"
          rows="10"
        ></textarea>
      </div>
      <div class="flex justify-between my-5">
        <input class="w-[230px]" type="date" />
        <p>~</p>
        <input class="w-[230px]" type="date" />
      </div>
      <div class="my-5">
        <button class="update-button">更新</button>
        <button class="delete-button">削除</button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "@vue/composition-api";
import { useRoute, useRouter } from "@/router/use-router";
import { Todo } from "@/interface/todo";

export default defineComponent({
  setup() {
    const route = useRoute();
    const router = useRouter();

    /**
     * ローカルストレージのデータを取得・保持
     */

    /**
     * 予定の更新処理
     */

    /**
     * 予定の削除処理
     */

    return {};
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
.update-button {
  @apply bg-green-700 text-white;
}
.delete-button {
  @apply bg-red-700 text-white;
}

.update-button,
.delete-button {
  transition: all ease 0.2s;
  @apply font-semibold py-2 px-3 rounded mx-5 w-[100px];
}
</style>

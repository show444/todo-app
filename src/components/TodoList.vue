<template>
  <div class="flex justify-center">
    <div class="w-[500px] text-left">
      <p :class="{ 'line-through': props.todo.status === 2 }">
        {{ props.todo.title }}
      </p>
      <p>{{ props.todo.startDate }} ~ {{ props.todo.endDate }}</p>
    </div>
    <div class="button-area">
      <button
        @click="$router.push(`/detail/${props.todo.id}`)"
        class="py-2 px-3 rounded bg-green-700 text-white font-semibold"
      >
        詳細
      </button>
      <button
        v-if="props.todo.status === 0"
        class="py-2 px-3 border border-solid rounded"
      >
        未着手
      </button>
      <button
        v-else-if="props.todo.status === 1"
        class="py-2 px-3 bg-yellow-500 text-white font-semibold rounded"
      >
        作業中
      </button>
      <button
        v-else
        class="py-2 px-3 bg-red-700 text-white font-semibold rounded"
      >
        完了
      </button>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "@vue/composition-api";
import { Todo } from "@/interface/todo";

interface Props {
  todo: Todo;
}

export default defineComponent<Props>({
  props: {
    todo: {
      type: Object as () => {
        id: {
          type: number;
          required: true;
        };
        status: {
          type: number;
          required: true;
        };
        title: {
          type: string;
          required: true;
        };
        description: {
          type: string;
          required: true;
        };
        startDate: {
          type: string;
          required: true;
        };
        endDate: {
          type: string;
          required: true;
        };
      },
      required: true,
    },
  },
  setup(props, context) {
    /**
     * ステータス更新
     */

    return {
      props,
    };
  },
});
</script>
<style lang="postcss" scoped>
button {
  @apply w-[80px] mx-2;
}

p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>

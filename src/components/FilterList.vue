<template>
  <div class="filter-area">
    <ul>
      <li>
        <label for="all">すべて</label>
        <input
          type="radio"
          v-model="filter"
          name="filter"
          id="all"
          value="3"
          checked
        />
      </li>
      <li>
        <label for="not-yet">未着手</label>
        <input
          type="radio"
          v-model="filter"
          name="filter"
          id="not-yet"
          value="0"
        />
      </li>
      <li>
        <label for="working">作業中</label>
        <input
          type="radio"
          v-model="filter"
          name="filter"
          id="working"
          value="1"
        />
      </li>
      <li>
        <label for="completed">完了</label>
        <input
          type="radio"
          v-model="filter"
          name="filter"
          id="completed"
          value="2"
        />
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "@vue/composition-api";

export default defineComponent({
  props: {
    filterStatus: {
      type: String,
      required: true,
    },
  },
  setup(props, { emit }) {
    const filter = ref(props.filterStatus);

    /**
     * フィルターの更新処理
     */

    return {
      filter,
    };
  },
});
</script>

<style lang="postcss" scoped>
.filter-area {
  @apply my-10;
}
.filter-area ul {
  @apply flex justify-center items-center;
}
.filter-area li {
  @apply px-4;
}
</style>

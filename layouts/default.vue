<template>
  <Todos />
</template>

<script>
import { useFiltersStore } from "~/store/todos";

import Todos from "@/components/Todos.vue";
export default {
  components: {
    Todos,
  },
  setup() {
    const todo = ref("");
    const filtersStore = useFiltersStore();
    // const filtersList = filtersStore.filtersList;
console.log(filtersStore)
    return { todo };
  },
};
</script>

<style lang="scss" scoped></style>

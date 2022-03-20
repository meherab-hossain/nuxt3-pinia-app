<template>
  <div>
    <div>
      <div style="display: flex;">
        <div>
          <input v-model="todo" placeholder="Type todo" @keyup.enter="add()" />
        </div>
        <div>
          <button @click="add">Add</button>
        </div>
      </div>
      <ul>
        <li v-for="(item, index) in todos" :key="index">
          <input
            @change="onchange(index)"
            type="checkbox"
            :checked="item.complete"
          />
          {{ item.text }}
          <button @click="deleteTodo(index)">Delete</button>
        </li>
      </ul>
    </div>
    <div>Number of completed todo: {{ totoalCompletedTodos }}</div>
  </div>
</template>

<script>
import { reactive, toRefs, ref, computed } from "vue";

export default {
  setup() {
    const todo = ref("");

    const todos = ref([
      {
        id: 1,
        text: "hello",
        complete: false,
      },
    ]);

    const onchange = (i) => {
      todos.value[i].complete = !todos.value[i].complete;
    };

    const add = () => {
      todos.value = [
        {
          id: 1,
          text: todo.value,
          complete: false,
        },
        ...todos.value,
      ];
      todo.value = ""
    };

    function deleteTodo(i) {
      todos.value.splice(i, 1);
    }

    const totoalCompletedTodos = computed(() => {
      const array = todos.value.filter((item) => item.complete === true);
      return array?.length || 0;
    });

    return {
      todos,
      todo,
      deleteTodo,
      onchange,
      add,
      totoalCompletedTodos,
    };
  },
};
</script>

<style lang="scss" scoped></style>

<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todoEl, i) of todosData"
        v-bind:todo="todoEl"
        v-bind:key="todoEl.id"
        v-bind:idx="i + 1"
        @completeChange="completeChange"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem';
export default {
  components: {
    TodoItem,
  },

  data() {
    return {
      todosData: [
        { id: 1, title: 'Learn vue.js', completed: false },
        { id: 2, title: 'Made TodoApp', completed: true },
        { id: 3, title: 'Be happy', completed: false },
      ],
    };
  },

  methods: {
    completeChange({ isCompleted, objId }) {
      console.log(isCompleted, objId);
      this.todosData.find(o => o.id === objId).completed = !isCompleted;
      //   this.todosData.completed = !isCompleted;
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>
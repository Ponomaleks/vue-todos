<template>
  <li>
    <span v-bind:class="{ done: todo.completed }">
      <input type="checkbox" v-on:change="onCompleteChange" />
      <strong>{{ idx }}</strong>
      {{ todo.title }}
    </span>
    <button type="button">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    idx: {
      type: Number,
      required: true,
    },
  },

  methods: {
    onCompleteChange() {
      this.$emit('completeChange', {
        isCompleted: this.todo.completed,
        objId: this.todo.id,
      });
    },
  },

  emits: ['completeChange'],
};
</script>


<style scoped>
li {
  border: solid grey;
  border-radius: 1em;
  padding: 10px;
  margin: 10px;
  display: inline-block;
  box-shadow: rgb(85, 81, 81) 0.2em 0.3em 0.2em;
}
li:hover {
  transform: scale(1.03) translate(-2px, -2px);
  transition: 250ms;
}

button {
  margin-left: 15px;
  border: solid 1px grey;
  border-radius: 50%;

  font-size: 20px;
  color: #fff;
  background-color: orangered;
}
button:hover {
  background-color: rgb(255, 0, 0);
  transform: scale(1.01);
}

input {
  margin-right: 1rem;
}

.done {
  text-decoration: line-through;
}
</style>
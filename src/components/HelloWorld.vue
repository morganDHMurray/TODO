<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      For a guide and recipes on how to configure / customize this project,<br />
      check out the
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener"
        >vue-cli documentation</a
      >.
    </p>
    <div class="list">
      <input type="text" v-model="input" />
      <button type="button" v-on:click="addItem" ref="button">Add</button>
      <p>{{ error }}</p>
      <ul>
        <todo-item
          v-for="(item, index) in todoItems"
          :key="index"
          :id="index"
          v-model="item.done"
          :description="item.description"
        />
      </ul>
      <span>{{ leftTodo }}</span>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  components: {
    TodoItem
  },
  name: "HelloWorld",
  props: {
    msg: String
  },
  data: () => ({
    todoItems: [],
    input: "",
    error: ""
  }),
  methods: {
    addItem() {
      if (this.input.length === 0) {
        this.error = "Ya fool, enter a value";
        return;
      }

      this.error = "";

      const newItem = {
        description: this.input,
        done: false
      };

      this.todoItems.push(newItem);
      this.input = "";
    }
  },
  computed: {
    leftTodo() {
      return this.todoItems.reduce((acc, { done }) => {
        return !done ? acc + 1 : acc;
      }, 0);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.hello {
  width: 100%;
}
.list {
  margin: 5rem auto;
  color: purple;
  text-align: left;
}

.list ul {
  list-style: none;
}
</style>

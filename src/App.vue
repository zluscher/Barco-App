<template>
  <div
    id="app"
    class="min-h-screen w-full bg-gray-300 flex flex-col items-center"
  >
    <button
      @click="triggerTransition"
      class="my-5 bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
    >
      Refresh
    </button>
    <template v-if="showusers">
      <staggered-fade
        :duration="150"
        tag="ul"
        class="flex flex-col w-full items-center max-w-xl"
      >
        <!-- Each element requires a data-index attribute in order for the transition to work properly -->
        <card
          v-for="(user, index) in users"
          :user="user"
          :data-index="index"
          :key="user.name"
        />
        <TodoList
          v-for="(todo, index) in todos"
          :todo="todo"
          :data-index="index"
          :key="todo.name"
        />
      </staggered-fade>
    </template>
  </div>
</template>

<script>
import Card from "./components/Card";
import StaggeredFade from "./components/StaggeredFade";
import TodoList from "./components/TodoList.vue";
import $ from "jquery";
import user from "../users.json";
import todos from "../todos.json";
var randomColor = Math.floor(Math.random() * 16777215).toString(16);
export default {
  name: "App",
  components: {
    Card,
    TodoList,
    StaggeredFade,
  },

  // mounted() {
  //   $(document).ready(function () {
  //     $.getJSON("../users.json", function (data) {
  //       var arrItems = [];
  //       $.each(data, function (index, value) {
  //         arrItems.push(value);
  //         return { arrItems };
  //       });
  //     });
  //   });
  // },

  // json1.map(x => Object.assign(x, json2.find(y => y.id == x.id)));

  // async fetchUsers () {
  // const res = await fetch('http://localhost:5000/tasks')
  // const data = await res.json()
  // return DataTransfer
  // },

  data() {
    return {
      showusers: true,
      myJson: user,
      myJson2: todos,
      users: user,
      todos: todos,
      color: randomColor,
    };
  },
  methods: {
    triggerTransition() {
      this.showusers = false;
      this.$nextTick(() => {
        this.showusers = true;
      });
    },
    // toggleAddTask() {
    //   this.showAddTask = !this.showAddTask;
    // },
    // async addTask(task) {
    //   const res = await fetch("/tasks", {
    //     method: "POST",
    //     headers: {
    //       "Content-type": "application/json",
    //       body: JSON.stringify(task),
    //     },
    //   });
    // },
  },
};
</script>

<style>
</style>

<template>
  <li
    class="bg-white shadow-lg py-3 px-5 rounded-lg flex justify-between w-full mb-6"
  >
    <button
      @click="$router.push({ path: '/Profile.vue' })"
      class="bg-300 hover:bg-green-200 text-white py-0.1 px-2 rounded-full"
    >
      <div class="flex p-1 flex space-x-4 items-center">
        <img src="https://picsum.photos/200" class="w-12 h-12 rounded-full" />
        <div class="ml-3">
          <p class="text-gray-900 font-sans tracking-wide text-sm">
            {{ user.name }}
          </p>
          <p class="text-gray-900 font-sans tracking-wide text-sm">
            {{ user.email }}
          </p>
          <p class="text-gray-900 font-sans tracking-wide text-sm">
            {{ user.phone }}
          </p>
          <p class="text-gray-900 font-sans tracking-wide text-sm">
            {{ user.website }}
          </p>
        </div>
      </div>
    </button>
    <div class="flex-auto w-32 h-full">
      <div class="flex-grow">
        <badge :color="user.color">{{ user.company.catchPhrase }}</badge>
        <TodoList class="text-gray-900 font-sans tracking-wide text-sm" />
      </div>
    </div>
  </li>
</template>
<script>
import Badge from "./Badge";
import TodoList from "./TodoList";
export default {
  components: {
    Badge,
    TodoList,
  },
  props: {
    user: {
      type: Object,
      default: () => ({}),
    },
  },
};
</script>

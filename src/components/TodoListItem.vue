<template>
  <li>
    <button
      @click="$emit('remove', todo.id)"
      class="bg-red-300 hover:bg-red-400 text-white py-0.1 px-2 rounded-full"
    >
      X
    </button>
    {{ todo.text }}
  </li>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>
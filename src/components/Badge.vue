<template>
      
<div
    class="px-4 h-6 rounded-full text-xs font-semibold flex items-center cursor-pointer truncate"
    :class="`bg-${color}-100 text-${color}-700 hover:bg-${color}-500 hover:text-white`"
  >  
    
    <span v-if="showDot" class="w-2 h-2 rounded-full mr-1" :class="`bg-${color}-400`"></span>
    <slot></slot>
  </div></button>
</template>
<script>
export default {
  props: {
    color: {
      type: String,
      default: "teal",
    },
    showDot: {
      type: Boolean,
      default: true,
    },
  },
};
</script>

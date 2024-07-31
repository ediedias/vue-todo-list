<script setup>
defineProps({
     task: {
          type: Object,
          require: true
     }
});
</script>

<template>
     <li class="flex justify-between items-center mb-2">
          <span :class="{ 'line-through': task.completed }" @click="$emit('toggle')" class="cursor-pointer">{{ task.text }}</span>
          <button @click="$emit('remove')" class="text-red-500">Remove</button>
     </li>
</template>

<style scoped>
.line-through {
     text-decoration: line-through;
}
</style>
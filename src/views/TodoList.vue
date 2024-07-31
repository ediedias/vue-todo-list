<script setup>
import { ref } from 'vue';
import TodoItem from '../components/TodoItem.vue';

const newTask = ref([]);
const tasks = ref([]);

const addTask = () => {
     if (newTask.value.trim()) {
          tasks.value.push({ text: newTask.value, completed: false });
          newTask.value = '';
     }
};

const removeTask = (index) => {
     tasks.value.splice(index, 1);
};

const toggleTask = (index) => {
     tasks.value[index].completed = !tasks.value[index].completed;
};

</script>

<template>
     <div class="mb-4 w-full">
          <input v-model="newTask" @keyup.enter="addTask" class="border p-2 w-full box-border" type="text" placeholder="Add a new task" />
          <ul>
               <TodoItem v-for="(task, index) in tasks" :key="index" :task="task" @remove="removeTask(index)" @toggle="toggleTask(index)" />
          </ul>
     </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from 'vue';
import TodoVue from './components/Todo.vue';
import TodoList from './components/TodoList.vue';

const message = ref<any[]>([]);

// Load data from local storage on component mount
onMounted(() => {
  loadFromLocalStorage();
});

const saveToLocalStorage = () => {
  localStorage.setItem('message', JSON.stringify(message.value));
};

const loadFromLocalStorage = () => {
  const storedMessage = localStorage.getItem('message');
  if (storedMessage) {
    message.value = JSON.parse(storedMessage);
  }
};

const insertData = (data: string) => {
  message.value.push(data);
  saveToLocalStorage();
};

const checkBoxValue = (data: string, value: boolean) => {
  const item = message.value.find(item => item.data === data);
  if (item) {
    item.checked = value; // Update the 'checked' property of the item
    saveToLocalStorage();
  }
}

const deleteData = (data: string) => {
  message.value = message.value.filter(item => item !== data);
  saveToLocalStorage();
};

</script>

<template>
  <div class="p-4 max-w-max md:max-w-screen-sm mx-auto">
    <h1 class="text-4xl font-bold py-6">Todo List By Vue <img src="./assets/logo.svg" width="40" height="40"
        class="inline-block" /></h1>
    <TodoVue @save="insertData" />
    <div v-if="message.length > 0" class="mt-10">
      <TodoList :message="message" @checked="checkBoxValue" @delete="deleteData" />
    </div>
  </div>
</template>

<script  lang="ts">
import TodoVue from './components/Todo.vue';

import TodoList from './components/TodoList.vue';
export default {
  name: "App",
  components: {
    TodoVue,
    TodoList
  },
  data() {
    return {
      message: []
    }

  },
  methods: {
    insertData(data: string) {
      //@ts-ignore
      this.message.push(data)
    },
    deleteData(id: any) {
      this.message = this.message.filter(item => {
        //@ts-ignore
        return item.id !== id
      })
    }
  }
}


</script>


<template>
  <div class="m-8 max-w-screen-sm mx-auto">
    <h1 class="text-4xl font-bold py-6">Todo List By Vue <img src="./assets/logo.svg" width="40" height="40"
        class="inline-block" /></h1>
    <TodoVue @save="insertData" />
    <div v-if="message.length > 0" class="mt-10">
      <TodoList :message="message" @delete="deleteData" />
    </div>
  </div>
</template>

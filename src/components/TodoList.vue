
<script lang="ts">
export default {
    name: "TodoList",
    props: ["message"],
    methods: {
        deleteMessage(id: any) {
            this.$emit("delete", id)
        }
    }
}
</script>

<template>
    <div>
        <h1 class="text-lg font-semibold">Todo List</h1>
        <ul>
            <li v-for="(data, idx) in message" :key="idx" class="p-4 shadow-lg flex justify-between">{{ data }} <button
                    @click="deleteMessage(idx)">Delete</button></li>
        </ul>
    </div>
</template>

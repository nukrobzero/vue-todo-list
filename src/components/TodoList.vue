<script setup lang="ts">


const emit = defineEmits(["delete", "checked"])
const props = defineProps(["message"])

const deleteMessage = (data: string) => {
    emit("delete", data)
}

const checked = (data: string, value: boolean) => {
    emit("checked", data, value)
}

</script>

<template>
    <div>
        <h1 class="text-lg font-semibold">Todo List</h1>
        <ul>
            <li v-for="(item, idx) in props.message" :key="idx" class="p-4 shadow-lg flex justify-between">
                <span class="flex items-center justify-center">
                    <input type="checkbox" v-model="item.checked" @change="checked(item.data, item.checked)" class="mr-2" />
                    <span :class="{ 'line-through': item.checked }">{{ item.data }}</span>
                </span>
                <button @click="deleteMessage(item)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<script setup  lang="ts">
import { ref } from 'vue';


const message = ref({ data: '', checked: false })
const emit = defineEmits(['save'])

const submitForm = () => {
    emit('save', message.value)
    message.value = { data: '', checked: false };

}

</script>



<template>
    <div>
        <form @submit.prevent="submitForm" class="flex flex-col space-y-4">
            <label for="message" class="text-xl font-semibold">Message:</label>
            <input type="text" v-model.trim="message.data" placeholder="type..."
                class="border border-gray-500 rounded-md p-2" required />
            <button type="submit" class="bg-blue-600 hover:bg-blue-400 text-white p-2 rounded-md">Submit</button>
        </form>
    </div>
</template>

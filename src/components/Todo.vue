<script  lang="ts">

export default {
    name: "Todo",
    data() {
        return {
            message: ""
        }
    },
    methods: {
        submitForm() {
            this.$emit("save", this.message);
            this.message = "";
        }
    }

}
</script>



<template>
    <div>
        <form @submit.prevent="submitForm" class="flex flex-col space-y-4">
            <label for="message" class="text-xl font-semibold">Message:</label>
            <input type="text" v-model.trim="message" placeholder="type..." class="border border-gray-500 rounded-md p-2" />
            <button type="submit" class="bg-blue-600 hover:bg-blue-400 text-white p-2 rounded-md">Submit</button>
        </form>
    </div>
</template>

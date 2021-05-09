<template>
    <div class="m-auto">
        <form class="w-full max-w-sm m-auto">
            <div class="flex items-center border-b border-teal-500 py-2">
                <input
                    v-model="newTodo"
                    class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                    type="text"
                    placeholder="Jane Doe"
                    aria-label="Full name"
                />
                <button
                    @click.prevent="onEvent"
                    class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-gray py-1 px-2 rounded"
                    type="button"
                >
                    Add
                </button>
                <button
                    @click.prevent="delTodo"
                    class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-gray py-1 px-2 rounded"
                    type="button"
                >
                    Del
                </button>
            </div>
        </form>

        <div class="m-auto">
            <ul class="max-w-sm m-auto">
                <li v-for="todo in todos" :key="todo">- {{ todo }}</li>
            </ul>
        </div>
    </div>
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
    data() {
        return {
            todos: ['list'],
            newTodo: '',
        };
    },
    methods: {
        onEvent(ev: UIEvent) {
            this.addTodo(this.newTodo);
        },
        addTodo(title: string) {
            this.todos.push(title);
        },
        delTodo() {
            if (this.todos.length > 0) {
                this.todos.splice(0, 1);
            }
        },
    },
});
</script>

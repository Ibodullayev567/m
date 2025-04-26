<template>
  <div class="min-h-screen bg-blue-600 flex items-center justify-center p-6">
    <div class="bg-white shadow-lg rounded-lg p-6 w-full max-w-md">
      <h1 class="text-2xl font-bold text-center text-gray-800 mb-4">ToDo List</h1>
      <div class="flex gap-2 mb-4">
        <input
            v-model="newTask"
            @keyup.enter="addTask"
            type="text"
            placeholder="Enter your task..."
            class="flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring focus:ring-blue-300"
        />
        <button
            @click="addTask"
            :disabled="!newTask.trim()"
            class="px-4 py-2 bg-blue-500 text-white font-semibold rounded-lg hover:bg-blue-600 disabled:opacity-100 disabled:cursor-not-allowed"
        >
          Add
        </button>
      </div>
      <ul class="space-y-2">
        <li
            v-for="(task, index) in tasks"
            :key="index"
            class="flex justify-between items-center p-3 bg-blue-100 rounded-lg"
        >
          <span class="text-gray-800">{{ task }}</span>
          <button
              @click="deleteTask(index)"
              class="p-2 bg-blue-100 text-white rounded-lg"
          >
            <div class="w-12 h-12 bg-blue-800 flex items-center justify-center center rounded-lg">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M7 21C6.45 21 5.97933 20.8043 5.588 20.413C5.19667 20.0217 5.00067 19.5507 5 19V6H4V4H9V3H15V4H20V6H19V19C19 19.55 18.8043 20.021 18.413 20.413C18.0217 20.805 17.5507 21.0007 17 21H7ZM17 6H7V19H17V6ZM9 17H11V8H9V17ZM13 17H15V8H13V17Z" fill="white"/>
              </svg>
            </div>
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.unshift(this.newTask.trim());
        this.newTask = "";
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
@import "./assets/tailwind.css";
</style>

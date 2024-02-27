<!-- Modal.vue -->
<script setup>
  import { ref } from 'vue';

// Define props using `defineProps`
const { show, close, submit, editedTask } = defineProps(['show', 'close', 'submit', 'editedTask']);

  </script>
<template>
    <div class="fixed inset-0 z-50 flex items-center justify-center w-full overflow-hidden main-modal h-100 animated fadeIn faster" v-if="show" style="background: rgba(0,0,0,.7);">
      <div class="z-50 w-11/12 mx-auto overflow-y-auto bg-white border border-teal-500 rounded shadow-lg modal-container md:max-w-md">
        <div class="px-6 py-4 text-left modal-content">
          <!-- Title and Close Button -->
          <div class="flex items-center justify-between pb-3">
            <p class="text-2xl font-bold text-black">Edit Task</p>
            <div class="z-50 cursor-pointer modal-close" @click="close">
              <svg class="text-black fill-current" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 18 18">
                <path d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"></path>
              </svg>
            </div>
          </div>
          <!-- Edit Task Form -->
          <div class="my-5">
            <form @submit.prevent="submit">
              <label for="editName" class="text-black">Name:</label>
              <input v-model="editedTask.name" type="text" id="editName" class="w-full px-3 py-2 text-black border rounded shadow appearance-none" required>
              <br><br>
              <label for="editTime" class="text-black">Time:</label>
              <input v-model.number="editedTask.time" type="number" id="editTime" class="w-full px-3 py-2 mb-3 text-black border rounded shadow appearance-none" required>
              <button type="submit" class="px-4 py-2 font-bold text-white bg-blue-600 rounded hover:bg-blue-800">Submit</button>
              <button @click="close" type="button" class="px-4 py-2 ml-3 font-bold text-white bg-red-600 rounded hover:bg-red-800">Cancel</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  
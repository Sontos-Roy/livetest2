<template>
  <div class="max-w-lg p-8 mx-auto my-10 bg-white shadow rounded-xl shadow-slate-300">
    <div class="flex flex-row items-center justify-between">
      <div>
        <h1 class="text-3xl font-medium text-black">Tasks list</h1>
      </div>
    </div>
    <p class="text-slate-500">Hello, here are your latest tasks</p>

    <div id="tasks" class="my-5">
      <div id="task" v-for="(task, index) in tasks" :key="index" class="flex items-center justify-between px-2 py-3 border-b border-l-4 border-slate-200 border-l-transparent bg-gradient-to-r from-transparent to-transparent hover:from-slate-100">
        <div class="inline-flex items-center space-x-2 text-black">
          <div>
            <i class="fa fa-check-circle"></i>                     
          </div>
          <div>{{ task.name }} (Time : {{ task.time }})</div>
        </div>
        <div @click="openEditPopup(index)" class="px-4 py-2 font-bold text-white bg-blue-100 rounded hover:bg-blue-300">
          <i class="text-black fa fa-edit"></i>                    
        </div>
      </div>
    </div>
  </div>

  <Modal :show="showPopup" :close="closeEditPopup">
    <form @submit.prevent="updateTask">
      <label for="editName" class="text-black">Name:</label>
      <input v-model="editedTask.name" type="text" id="editName" class="w-full px-3 py-2 border rounded shadow appearance-none text-grey-darker" required>
      <br><br>
      <label for="editTime" class="text-black">Time:</label>
      <input v-model.number="editedTask.time" type="number" id="editTime" class="w-full px-3 py-2 mb-3 border rounded shadow appearance-none text-grey-darker" required>
      <button type="submit" class="px-4 py-2 font-bold text-white bg-blue-600 rounded hover:bg-blue-800">Submit</button>
      <button @click="closeEditPopup" type="button" class="px-4 py-2 ml-3 font-bold text-white bg-red-600 rounded hover:bg-red-800">Cancel</button>
    </form>
  </Modal>
</template>

<script setup>
import { ref } from 'vue';
import Modal from './components/Modal.vue';

const tasks = ref([
  { name: 'Task 1', time: 30 },
  { name: 'Task 2', time: 40 },
  { name: 'Task 3', time: 60 },
  { name: 'Task 4', time: 45 },
  { name: 'Task 5', time: 50 },
]);

const showPopup = ref(false);
const editedTask = ref({ name: '', time: 0 });
const editedTaskIndex = ref(-1);

const openEditPopup = (index) => {
  editedTask.value = { ...tasks.value[index] };
  editedTaskIndex.value = index;
  showPopup.value = true;
};

const closeEditPopup = () => {
  showPopup.value = false;
  editedTask.value = { name: '', time: 0 };
  editedTaskIndex.value = -1;
};

const updateTask = () => {
  if (editedTaskIndex.value !== -1) {
    tasks.value[editedTaskIndex.value] = { ...editedTask.value };
    closeEditPopup();
  }
};
</script>
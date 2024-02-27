<!-- Modal.vue -->
<template>
    <teleport to="body">
      <div class="fixed inset-0 z-50 flex items-center justify-center w-full overflow-hidden main-modal h-100 animated fadeIn faster" v-if="show" style="background: rgba(0,0,0,.7);">
        <div class="z-50 w-11/12 mx-auto overflow-y-auto bg-white border border-teal-500 rounded shadow-lg modal-container md:max-w-md">
          <div class="px-6 py-4 text-left modal-content">
            <!--Title-->
            <div class="flex items-center justify-between pb-3">
              <p class="text-2xl font-bold text-black">Edit Task</p>
              <div class="z-50 cursor-pointer modal-close" @click="close">
                <svg class="text-black fill-current" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 18 18">
                  <path d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"></path>
                </svg>
              </div>
            </div>
            <!--Body-->
            <div class="my-5">
              <slot></slot>
            </div>
          </div>
        </div>
      </div>
    </teleport>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const { show, close } = props;
  </script>
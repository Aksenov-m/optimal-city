<script setup>

import { ref } from 'vue';

const newMessage = ref('');

const emit = defineEmits(["onSubmit"])

// emit('response', newMessage)

// defineProps(['newMessage'])
// defineEmits(['update:newMessage'])



function buttonClick() {
  emit('onSubmit', newMessage);
  newMessage.value = ""
}

</script>

<template>
    <div class="input">
      <input type="text" v-model="newMessage" placeholder="Type your message..." />
      <button @click='buttonClick'>Send</button>
    </div>
  </template>
  

  <style scoped>
  .input {
    display: flex;
    gap: 10px;
  }
  
  .input input {
    flex: 1;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .input button {
    padding: 8px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  </style>
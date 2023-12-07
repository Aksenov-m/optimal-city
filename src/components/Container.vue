<script setup>
import Avatar from "./Avatar.vue";
import Input from "./Input.vue";
import Message from "./Message.vue";

</script>

<template>
    <div class="chat-container">
      <Avatar />
      <div class="chat-content">
        <Message />
        <Input />
      </div>
    </div>
  </template>
  
  
  <style scoped>
  .chat-container {
    display: flex;
    flex-direction: column;
    max-width: 400px;
    margin: auto;
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  
  .chat-content {
    margin-top: 15px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  </style>
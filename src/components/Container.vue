<script setup>
import Avatar from './Avatar.vue';
import Input from './Input.vue';
import Message from './Message.vue';

import avatarChat from "../images/avatar-chat.jpg";
import avatarUser from "../images/avatar.jpg";
</script>

<template>
  <div class="chat-container">
    <!-- <Avatar :src="avatarChat" /> -->
    <div class="chat-content">
      <Message :isSelf="true" :avatar="avatarUser">Hello there!</Message>
      <Message :isSelf="false" :avatar="avatarChat">Hi! How are you?</Message>
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
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.chat-content {
  margin-top: 15px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
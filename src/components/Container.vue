<script setup>
import { ref } from 'vue'
import Input from './Input.vue';
import Message from './Message.vue';

import avatarChat from "../images/avatar-chat.jpg";
import avatarUser from "../images/avatar.jpg";

// const newMessage = ref('');

const messages = ref([
])

function callback(event) {
  messages.value.push({ text: event.value, isSelf: true });
  console.log(messages)
}

// const dataMessage = [
//   "Привет! Что я могу для Вас сделать?",
//   "Заказать пиццу",
//   "Установить будильник",
//   "Вывести погоду",
// ];


</script>

<template>
  <div class="chat-container">
    <!-- <Avatar :src="avatarChat" /> -->
    <div class="chat-content">
      <Message :isSelf="false" :avatar="avatarChat"></Message>
      <Message  v-for="newMessage in messages"
      :key="newMessage" :isSelf=newMessage.isSelf :avatar="avatarUser">{{newMessage.text}}</Message>
      <Input @on-submit="callback" />
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
<script setup>
import { ref, reactive, watchEffect } from "vue";
import Input from "./Input.vue";
import Message from "./Message.vue";
import WelcomeMessage from "./WelcomeMessage.vue";

import avatarChat from "../images/avatar-chat.jpg";
import avatarUser from "../images/avatar.jpg";

// const newMessage = ref('');

const messages = reactive([]);

function callback(event) {
  messages.push({ text: event.value || event, isSelf: true });
}

watchEffect(() => {
  const arr = [...messages];
  const lastMessage = arr[arr.length - 1];

  if (lastMessage && lastMessage.isSelf) {
    setTimeout(() => {
      messages.push({
        text: "Извините, бот находится в режиме разработки",
        isSelf: false,
      });
    }, 1000);
  }
});


</script>

<template>
  <div class="chat-container" @dragstart="onDragstart($event,)">
    <div class="chat-content">
      <Message :isSelf="false" :avatar="avatarChat"
        >Привет! Что я могу для Вас сделать?</Message
      >
      <WelcomeMessage @on-click="callback" />
      <div class="messages">
        <Message
          v-for="newMessage in messages"
          :key="newMessage"
          :isSelf="newMessage.isSelf"
          :avatar="newMessage.isSelf ? avatarUser : avatarChat"
          >{{ newMessage.text }}</Message
        >
      </div>

      <Input @on-submit="callback" />
    </div>
  </div>
</template>

<style scoped>
.chat-container {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: auto;
  padding: 10px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 2px 25px #1a1a1a;
  overflow: hidden;
  position: relative;
  z-index: 5;
  width: 100%;
  min-width: 300px;
  min-height: 290px;
  /* box-shadow: 0 0 30px rgba(0, 0, 0, 0.1); */
}

.chat-content {
  width: 100%;
  margin-top: 15px;
  display: flex;
  flex-direction: column;
  height: 513px;
  overflow-y: auto;
}

.messages {
  margin-bottom: 55px;
  display: flex;
  flex-direction: column;
  gap: 13px;
}
</style>

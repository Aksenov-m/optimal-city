<script setup>
import { computed } from 'vue';

import Avatar from './Avatar.vue';



const props = defineProps(["avatar", "isSelf" ]);



const hasAvatar =  computed(() => !!props.avatar)



</script>

<template>
  <div class="message" :class="{ 'self': props.isSelf, 'bot': !props.isSelf }">
    <Avatar v-if="hasAvatar" :src="props.avatar" />
    <div class="message-content">
      <p class="message-bubble">
        <!-- Здесь используем слот для вставки содержимого сообщения -->
        <slot></slot>
      </p>
    </div>
  </div>
</template>


<style scoped>
.message {
  display: flex;
  max-width: 95%;
}

.self {
  flex-direction: row-reverse; /* Меняем порядок элементов для самописных сообщений */
  margin-left: auto; /* Смещение сообщения вправо, если оно самописное */
}

.bot {
  flex-direction: row; /* Оставляем аватар чатбота слева */
}

.message-content {
  margin-left: 10px; /* Добавляем отступ между аватаром и контентом сообщения */
  display: flex;
  flex-direction: column;
}

.message-bubble {
  margin-top: 5px; /* Добавляем отступ между аватаром и сообщением */
  padding: 10px;
  background-color: #007bff; /* Цвет фона сообщения как в iMessage */
  color: #fff; /* Цвет текста */
  border-radius: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  word-wrap: break-word;
}
</style>
<script setup>
import { computed } from "vue";

import Avatar from "./Avatar.vue";

const props = defineProps(["avatar", "isSelf"]);

const hasAvatar = computed(() => !!props.avatar);
</script>

<template>
  <div class="message" :class="{ self: props.isSelf, bot: !props.isSelf }" v-cloak>
    <Avatar v-if="hasAvatar" :src="props.avatar" :isSelf="props.isSelf" />
    <div class="message-content">
      <p class="message-bubble" :class="{ 'bubble-self': props.isSelf, 'bubble-bot': !props.isSelf }">
        <!-- Здесь используем слот для вставки содержимого сообщения -->
        <slot></slot>
      </p>
    </div>
  </div>
</template>

<style scoped>

[v-cloak] {
  display: none;
}
.message {
  display: flex;
  align-items: end;
  max-width: 100%;
  justify-content: end;
}

.self {
  flex-direction: row-reverse; /* Меняем порядок элементов для самописных сообщений */
  margin-left: 100px;
}

.bot {
  flex-direction: row; /* Оставляем аватар чатбота слева */
  margin-right: 100px;
}

.message-content {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.message-bubble {
  margin: 0;
  padding: 10px;
  background-color: #007bff; /* Цвет фона сообщения как в iMessage */
  color: #fff; /* Цвет текста */
  border-radius: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  word-wrap: break-word;
}

.bubble-bot {
  background-color: rgba(245, 245, 245, 1);
  color: #6d6d6d;
  border-radius: 15px 15px 15px 0; /* Убираем border-radius для нижнего левого угла */
}

.bubble-self {
  border-radius: 15px 15px 0 15px; /* Убираем border-radius для нижнего левого угла */
}
</style>

<script setup>
import { ref, onMounted } from 'vue';

const dataMessage = ref([
  "Заказать пиццу",
  "Установить будильник",
  "Вывести погоду",
]);

const delayedMessages = ref([]);

onMounted(async () => {
  for (let i = 0; i < dataMessage.value.length; i++) {
    await new Promise((resolve) => setTimeout(resolve, 1500)); // задержка 1 секунда
    delayedMessages.value = [...delayedMessages.value, dataMessage.value[i]];
  }
});

const emit = defineEmits(["onClick"])

function buttonClick(e) {
  emit('onClick', e.target.innerText);
}

</script>

<template>
  <div class="message-content">
    <p
    @click='buttonClick'
      class="message-bubble"
      v-for="(welcomeMessage, index) in delayedMessages"
      :key="index"
    >
      {{ welcomeMessage }}
    </p>
  </div>
</template>

<style scoped>
.message-content {
  display: flex;
  flex-direction: row;
}

.message-bubble {
  padding: 10px;
  background-color: #007bff; /* Цвет фона сообщения как в iMessage */
  color: #fff; /* Цвет текста */
  border-radius: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  word-wrap: break-word;
  cursor: pointer;
  margin-right: 5px;
}

.message-bubble:last-child {
  margin-right: 0;
}
</style>
<script setup>

 
</script>

<template >
    <div class="message">
      <div class="message-bubble">
        <!-- Здесь используем слот для вставки содержимого сообщения -->
        <slot></slot>
      </div>
    </div>
  </template>
  
  
  <style scoped>
  .message {
    padding: 10px;
    background-color: #ecf0f1;
    border-radius: 8px;
  }
  
  .message-bubble {
    /* Добавим немного отступа от краев сообщения */
    margin: 5px;
  }
  </style>
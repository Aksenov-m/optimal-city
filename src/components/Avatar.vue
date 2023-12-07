<script setup>

  </script>

<template>
    <div class="avatar">
      <!-- Здесь используем тег img для отображения аватара, подставив свои данные -->
      <img src="../images/avatar.JPG" alt="User Avatar" />
    </div>
  </template>
  
  
  <style scoped>
  .avatar {
    width: 40px;
    height: 40px;
    background-color: #3498db;
    border-radius: 50%;
    overflow: hidden;
  }
  
  .avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  </style>
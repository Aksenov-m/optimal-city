<script setup>


const props = defineProps(["src"]);

</script>

<template>
  <div class="avatar">
    <img :src="props.src" alt="User Avatar" />
  </div>
</template>


<style scoped>
.avatar {
  width: 30px;
  height: 30px;
  overflow: hidden;
  border-radius: 50%;
}

.avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}
</style>
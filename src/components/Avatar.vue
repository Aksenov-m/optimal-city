<script setup>


const props = defineProps(["src", "isSelf"]);

</script>

<template>
  <div class="avatar" :class="{ 'avatar-self': props.isSelf, 'avatar-bot': !props.isSelf }">
    <img :src="props.src" alt="Avatar" />
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

.avatar-self {
  margin-left: 5px;
}
.avatar-bot {
  margin-right: 5px;
}

</style>
<template>
    <UAvatar :src="photo" size="3xl" alt="my-profile-photo" height="200" class="profile-avatar" />
</template>

<script setup>
const app = useAppConfig();
const { data: { photo } } = app
</script>

<style scoped>
.profile-avatar :deep(img) {
  object-fit: cover;
  object-position: center;
}
</style>

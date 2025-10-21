<template>
    <UAvatar :src="photoUrl" size="3xl" alt="my-profile-photo" height="200" class="profile-avatar" />
</template>

<script setup>
const app = useAppConfig();
const { data: { photo } } = app

// Handle base URL for GitHub Pages deployment
const config = useRuntimeConfig();
const photoUrl = computed(() => {
  if (photo.startsWith('http')) {
    return photo;
  }
  const baseURL = config.app.baseURL || '/';
  return baseURL === '/' ? photo : `${baseURL}${photo}`.replace('//', '/');
});
</script>

<style scoped>
.profile-avatar :deep(img) {
  object-fit: cover;
  object-position: center;
}
</style>

<template>
<div class="container mt-4 mx-auto">
  <h1 class="font-bold text-3xl">File Upload</h1>
  <div class="my-2">
    <form action="https://httpbin.org/anything" id="image-upload-form" method="post">
      <div class="flex flex-col gap-2">
        <div>
          <input class="bg-gray-100 border rounded-lg p-2" multiple name="files" type="file" />
        </div>
        <div>
          <input class="bg-gray-100 border rounded-lg p-2" name="submit" type="submit" />
        </div>
      </div>
    </form>
  </div>
</div>
</template>

<script setup lang="ts">
/* vue */
import { onMounted } from 'vue';

onMounted(() => {
});
</script>

<style scoped>
</style>

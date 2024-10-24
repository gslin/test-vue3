<template>
<div class="container mt-4 mx-auto">
  <h1 class="font-bold text-3xl">File Upload</h1>
  <div class="my-2">
    <form>
      <div class="flex flex-col gap-4">
        <h2>Area</h2>
        <div>
          <file-pond
            allow-multiple="true"
            class="w-full"
            credits="false"
            label-idle="Drag files &amp; drag to here, or click this area"
            name="tFiles"
            ref="pond"
            server="https://httpbin.org/anything"
            :allow-reorder="true"
            :files="tFiles"
            :instant-upload="false"
          >
          </file-pond>
        </div>
        <div>
          <h2>Information</h2>

          <div class="flex gap-2">
            <textarea class="bg-gray-100 border font-mono h-[20rem] rounded-lg p-2 w-full" readonly>{{ pond }}</textarea>
            <textarea class="bg-gray-100 border font-mono h-[20rem] rounded-lg p-2 w-full" readonly>{{ JSON.stringify(tFiles?.files) }}</textarea>
          </div>
        </div>
        <div>
          <h2>Buttons</h2>
          <input
            class="bg-gray-100 border rounded-lg p-2"
            name="submit"
            type="submit"
            @click.prevent="uploadFiles"
          />
        </div>
      </div>
    </form>
  </div>
</div>
</template>

<script setup lang="ts">
/* vue */
import { ref } from 'vue';

/* 3rd-party */
import axios from 'axios';
import vueFilePond from 'vue-filepond';
import 'filepond/dist/filepond.min.css';
import FilePondPluginImagePreview from 'filepond-plugin-image-preview';
import 'filepond-plugin-image-preview/dist/filepond-plugin-image-preview.css';

/* refs */
const tFiles = ref([]);
const pond = ref();

/* handlers */
const uploadFiles = () => {
  const fd = new FormData();
  for (const file of pond.value.getFiles()) {
    console.log(file);
    fd.append('files[]', file.file);
  }

  axios.post('https://httpbin.org/anything', fd, {
    headers: {
      'Content-Type': 'multipart/form-data',
    },
  });
};

const FilePond = vueFilePond(FilePondPluginImagePreview);
</script>

<style scoped>
</style>

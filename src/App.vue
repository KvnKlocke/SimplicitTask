<template>
  <div class="d-flex">
      <Sidebar @open:modal="isModalOpen = true" :list-name="list"/>
      <RouterView />
  </div>
  <CreateListModal :is-open="isModalOpen" @close:modal="isModalOpen = false"/>
</template>

<script setup lang="ts">
import Sidebar from "@/components/sidebar/Sidebar.vue";
import CreateListModal from "@/components/sidebar/modal/CreateListModal.vue";
import { ref } from 'vue';

const isModalOpen = ref(false);

const list = ref('')

</script>

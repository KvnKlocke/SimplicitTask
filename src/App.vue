<template>
  <div class="d-flex">
      <Sidebar @open:modal="isModalOpen = true" :list-name="list"/>
      <RouterView />
  </div>
  <Modal :is-open="isModalOpen" @close:modal="isModalOpen=false" @push:list="value => list = value" />
</template>

<script setup lang="ts">
import Sidebar from "./components/sidebar/Sidebar.vue";
import Modal from "./components/modal/Modal.vue";
import { ref } from 'vue';

const isModalOpen = ref(false);

const list = ref('');

</script>

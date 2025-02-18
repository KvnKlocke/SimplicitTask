<template>
    <Modal title="Liste erstellen" :open="$props.isOpen" @close:modal="$emit('close:modal')" :backrop="true">
        <template #body>
            <div>
                Gib deiner Liste einen Namen
            </div>
            <div class="mt-3">
                <CFormInput :style="stylesInput" type="text" placeholder="Listenname" @update:model-value="value => listName = value"/>
            </div>
            <div class="mt-3">
                <CButton color="secondary" @click="$emit('close:modal')">Schließen</CButton>
                <CButton color="primary" @click="createList()">Liste erstellen</CButton>
            </div>
        </template>
    </Modal>
</template>
<script setup lang="ts">
import Modal from '@/components/modal/Modal.vue'
import { CFormInput, CButton } from '@coreui/vue'
import { ref, type Ref } from 'vue'

const isOpen = ref(false);

defineProps({
    isOpen: {
        type: Boolean,
        required: true,
    }
})


const stylesInput = {
    '--cui-body-color': 'white',
    '--cui-secondary-color': 'white'
}

const listName: Ref<string> = ref('');

function createList() {
    emits('push:list', listName);
    isOpen.value = false;
}
const emits = defineEmits(['push:list', 'close:modal'])
</script>
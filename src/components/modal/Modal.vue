<template>
    <CModal :backdrop="true" alignment="center" :keyboard="true" @close="$emit('close:modal')" :visible="isOpen" :style="stylesModal">
        <CModalHeader :close-button="false">
            <CModalTitle>Liste erstellen</CModalTitle>
        </CModalHeader>
        <CModalBody>
            <div>
                Gib deiner Liste einen Namen
            </div>
            <div class="mt-3">
                <CFormInput :style="stylesInput" type="text" placeholder="Listenname" @update:model-value="value => listName = value"/>
            </div>
        </CModalBody>
        <CModalFooter>
            <CButton color="secondary" @click="$emit('close:modal')">Schließen</CButton>
            <CButton color="primary" @click="createList()">Liste erstellen</CButton>
        </CModalFooter>
    </CModal>
</template>

<script setup lang="ts">
import { CModal, CModalHeader, CModalBody, CModalFooter, CButton, CModalTitle, CFormInput } from '@coreui/vue';
import { ref, type Ref } from 'vue';

defineProps({
    isOpen: {
        type: Boolean,
        required: true,
    }
})

function createList() {
    emits('push:list', listName);
    emits('close:modal');
}

const listName: Ref<string> = ref('');

const stylesModal = {
    '--cui-body-bg': '#212631',
    '--cui-modal-color': 'white'
}

const stylesInput = {
    '--cui-body-color': 'white',
    '--cui-secondary-color': 'white'
}

const emits = defineEmits(['close:modal', 'push:list'])
</script>
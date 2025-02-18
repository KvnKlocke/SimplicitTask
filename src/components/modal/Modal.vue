<template>
    <CModal :backdrop="$props.backrop" :alignment="$props.alignment" :keyboard="true" @close="$emit('close:modal')" :visible="$props.open" :style="stylesModal">
        <CModalHeader :close-button="false">
            <CModalTitle>{{ $props.title }}</CModalTitle>
        </CModalHeader>
        <CModalBody>
            <slot name="body"></slot>
        </CModalBody>
        <div v-if="$props.footer">
            <CModalFooter>
                <slot name="footer"></slot>
            </CModalFooter>
        </div>
    </CModal>
</template>

<script setup lang="ts">
import { CModal, CModalHeader, CModalBody, CModalFooter, CModalTitle } from '@coreui/vue';

defineProps({
    open: {
        type: Boolean,
        required: true,
    },
    backrop: {
        type: Boolean,
        required: false,
        default: false
    },
    alignment: {
        type: String,
        required: false,
        default: 'center'
    },
    title: {
        type: String,
        required: true,
    },
    footer: {
        type: Boolean,
        required: false,
        default: false
    }
})

const stylesModal = {
    '--cui-body-bg': '#212631',
    '--cui-modal-color': 'white'
}

const emits = defineEmits(['close:modal'])
</script>
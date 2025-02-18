<template>
    <CSidebar colorScheme="dark" class="vh-100">
        <CSidebarHeader class="border-bottom">
            SimplicitTask
        </CSidebarHeader>
        <CSidebarNav>
            <CNavTitle class="d-flex w-100 mt-0 justify-content-between align-items-center"><div class="mt-2">Meine Listen</div><div class="d-flex fs-3 pointer" @click="$emit('open:modal')">+</div></CNavTitle>
            <div v-if="$props.listName !== ''">
                <CNavItem href="#">
                    {{ $props.listName }}
                    <CBadge class="ms-auto" color="primary">NEW</CBadge>
                </CNavItem>
            </div>
            <!--
            <CNavGroup>
            <template #togglerContent>
                <CIcon  customClassName="nav-icon" icon="cil-puzzle"/> Nav dropdown
            </template>
            <CNavItem href="#">
                <span class="nav-icon"><span class="nav-icon-bullet"></span></span> Nav dropdown item
            </CNavItem>
            <CNavItem href="#">
                <span class="nav-icon"><span class="nav-icon-bullet"></span></span> Nav dropdown item
            </CNavItem>
            </CNavGroup> -->
        </CSidebarNav>
        <CSidebarFooter class="border-top">
            Copyright 2025
        </CSidebarFooter>
    </CSidebar>
</template>
  
<script setup lang="ts">
import { CSidebar, CSidebarFooter, CSidebarNav, CNavItem, CNavTitle, CSidebarHeader, CBadge } from '@coreui/vue';


    defineProps({
        listName: {
            type: String,
            required: true,
        }
    })

  defineEmits(['open:modal'])

</script>

<style scoped>
.pointer:hover {
    cursor: pointer !important;
    color: lightskyblue;
}
</style>
  
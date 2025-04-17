<template>
    <IconSvg />
    <ChangeTheme />
    <HeaderNavbar />

    <div class="d-flex flex-column h-100">
        <main class="flex-shrink-0">
        <div class="container">
            <RouterView />
        </div>
    </main> 
    </div>      

    <FooterBar />
</template>

<script setup lang="ts">
import { RouterView } from 'vue-router';

import IconSvg from './components/icons/IconSvg.vue'
import ChangeTheme from './components/layout/ChangeTheme.vue'
import HeaderNavbar from './components/layout/HeaderNavbar.vue'
import FooterBar from './components/layout/FooterBar.vue'
</script>
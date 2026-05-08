<script setup>
    import SiteHeader from '../components/layout/Site-Header.vue';
    import Footer from '../components/layout/Footer.vue';
    import { RouterView } from 'vue-router';
</script>

<template lang="html">
    <SiteHeader />
        <main>
            <RouterView />
        </main>
    <Footer />
</template>

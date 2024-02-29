<script setup lang="ts">
import { RouterView } from 'vue-router'
import Layout from '@/layouts/Layout.vue'
import Navigation from '@/components/navigation/Navigation.vue'
</script>

<template>
  <Layout>
    <Navigation />
    <RouterView />
  </Layout>
</template>

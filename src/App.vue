<template>
  <NavBar />

  <RouterView />
</template>

<script setup lang="ts">
import NavBar from "@/components/layout/NavBar.vue";
import { RouterView } from "vue-router";
</script>

<style scoped></style>

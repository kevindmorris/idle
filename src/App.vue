<template>
  <NavBar />
  <div class="container col-6 my-3">
    <RouterView />
  </div>
</template>

<script setup lang="ts">
import NavBar from "@/components/layout/NavBar.vue";
import { RouterView } from "vue-router";
</script>

<style scoped></style>

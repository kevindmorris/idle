<template>
  <NewActivityForm @on-submit="handleSubmit" />
  <hr />
  <h1 class="h4">Event</h1>
  <VueJsonPretty :data="event" />
</template>

<script setup lang="ts">
import NewActivityForm from "@/components/forms/NewActivityForm.vue";
import type { Event } from "@/types";
import { ref, type Ref } from "vue";
import VueJsonPretty from "vue-json-pretty";
import "vue-json-pretty/lib/styles.css";

const event: Ref<Event | null> = ref(null);

function handleSubmit(response: Event) {
  event.value = response;
}
</script>

<style scoped></style>

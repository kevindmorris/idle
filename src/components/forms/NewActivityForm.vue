<template>
  <form @submit.prevent="submit">
    <div class="mb-3">
      <label for="inputType" class="form-label">Type</label>
      <select class="form-select" id="inputType" aria-describedby="inputTypeHelp" v-model="type">
        <option v-for="e in types" :key="e" :value="e">{{ e }}</option>
      </select>
      <div id="inputTypeHelp" class="form-text">The kind of activity.</div>
    </div>
    <div class="mb-3">
      <label for="inputParticipants" class="form-label">Participants</label>
      <input
        class="form-control"
        id="inputParticipants"
        type="number"
        min="0"
        max="10"
        step="1"
        aria-describedby="inputParticipantsHelp"
        v-model="participants"
      />
      <div id="inputParticipantsHelp" class="form-text">The number of participants.</div>
    </div>
    <div class="mb-3">
      <label for="inputPrice" class="form-label">Price</label>
      <input
        class="form-control"
        id="inputPrice"
        type="number"
        min="0"
        max="10"
        step="1"
        aria-describedby="inputPriceHelp"
        v-model="price"
      />
      <div id="inputPriceHelp" class="form-text">
        The price of the activity. (Scale from 0 to 1)
      </div>
    </div>
    <div class="d-flex justify-content-start gap-1">
      <button class="btn btn-secondary btn-sm" @click.prevent="clear">Clear</button>
      <button type="submit" class="btn btn-primary btn-sm">Submit</button>
    </div>
  </form>
</template>

<script setup lang="ts">
import { Ref, ref } from "vue";

const types = [
  "education",
  "recreational",
  "social",
  "diy",
  "charity",
  "cooking",
  "relaxation",
  "music",
  "busywork"
];

const type: Ref<string> = ref("");
const participants: Ref<string> = ref("");
const price: Ref<string> = ref("");

const clear = () => {
  type.value = "";
  participants.value = "";
  price.value = "";
};

const submit = async () => {
  try {
    const response = await fetch(
      "http://www.boredapi.com/api/activity?" + new URLSearchParams({ type: type.value }),
      { method: "GET" }
    );
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log(error);
  }
};
</script>

<style scoped></style>

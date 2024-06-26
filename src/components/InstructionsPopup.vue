<template>
  <v-fade-transition hide-on-leave>
    <v-card
      v-if="dialog"
      append-icon="$close"
      class="mx-auto w-sm-75 w-100 ma-4 rounded-lg"
      elevation="24"
      color="purple-darken-4"
    >
      <div class="py-12 text-center pa-2">
        <v-icon
          class="mb-6"
          icon="mdi-camera-outline"
          size="128"
          color="white"
        ></v-icon>
        <div class="text-h5 text-sm-h4 font-weight-bold px-12">
          Click on a picture and copy its url to the clipboard
        </div>
        <div class="mt-6 text-body-2 text-sm-subtitle-1">
          On the left sidebar you can choose between color and black & white
        </div>
      </div>

      <v-divider></v-divider>

      <div class="pa-4 text-center">
        <v-btn
          class="text-none"
          color="medium-emphasis"
          min-width="92"
          variant="outlined"
          rounded
          @click="dialog = false"
        >
          Ok!
        </v-btn>
      </div>
    </v-card>
  </v-fade-transition>
</template>

<script setup>
import { ref, onMounted } from "vue";

const dialog = ref(false);

onMounted(() => {
  setTimeout(() => {
    dialog.value = true;
  }, 1000);
});
</script>

<style scoped>
.v-card {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 10;
  margin: 0;
  position: fixed;
}
</style>

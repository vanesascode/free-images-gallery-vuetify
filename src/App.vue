<template>
  <v-app>
    <SideBar @selectColorOption="onSelectColorOption" />
    <v-main>
      <ImageGallery :isWithColor="isWithColor" />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
// REF creates a REACTIVE reference to a value.
import { ref } from "vue";

const isWithColor = ref(true);

const onSelectColorOption = (isColor: boolean) => {
  isWithColor.value = isColor;
};
</script>

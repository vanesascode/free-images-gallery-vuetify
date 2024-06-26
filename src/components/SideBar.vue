<template>
  <v-navigation-drawer expand-on-hover rail>
    <v-list>
      <!-- v-bind directive (:) is used to bind variables to attributes. -->
      <v-list-item
        :prepend-avatar="avatarPic"
        subtitle="To use in your projects"
        title="Image Gallery"
      ></v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list density="compact" nav>
      <v-list-item
        prepend-icon="mdi-image"
        title="Color Gallery"
        value="color"
        @click="selectColorOption(true)"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-dialpad"
        title="Black & White Gallery"
        value="black-and-white"
        @click="selectColorOption(false)"
      ></v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup lang="ts">
const emits = defineEmits(["selectColorOption"]);

const selectColorOption = (isColor: boolean) => {
  emits("selectColorOption", isColor);
};

const avatarPic = import.meta.env.VITE_APP_AVATAR_PIC || "";
</script>

<style scoped>
.mdi-dialpad {
  background-color: blueviolet;
  color: blueviolet;
}
</style>

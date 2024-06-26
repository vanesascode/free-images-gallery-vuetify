<template>
  <InstructionsPopup />
  <v-card class="ma-5 pa-3">
    <v-row>
      <v-col cols="4" sm="3" md="2" lg="1" v-for="n in 200" :key="n">
        <v-card
          id="image-card"
          @click="
            copyUrl(
              `${imagesSrc}${n * 5 + 10}${
                props.isWithColor ? '' : '&grayscale'
              }`
            )
          "
        >
          <v-img
            :src="`${imagesSrc}${n * 5 + 10}${
              props.isWithColor ? '' : '&grayscale'
            }`"
            :lazy-src="`${imagesSrcLazy}${n * 5 + 10} ${
              props.isWithColor ? '' : '&grayscale'
            }`"
            aspect-ratio="1"
            cover
          >
            <template v-slot:error>
              <v-img
                class="mx-auto"
                height="300"
                max-width="500"
                :src="errorSrc"
                aspect-ratio="1"
                cover
              ></v-img>
            </template>
            <template v-slot:placeholder>
              <div class="d-flex align-center justify-center fill-height">
                <v-progress-circular
                  color="grey-lighten-4"
                  indeterminate
                ></v-progress-circular>
              </div>
            </template>
          </v-img>
        </v-card>
      </v-col>
    </v-row>
  </v-card>
</template>

<script setup lang="ts">
const props = defineProps<{ isWithColor: boolean }>();

const imagesSrc = import.meta.env.VITE_APP_SRC || "";
const imagesSrcLazy = import.meta.env.VITE_APP_SRC_LAZY || "";

const errorSrc = import.meta.env.VITE_APP_AVATAR_PIC || "";

const copyUrl = async (url: string) => {
  await navigator.clipboard.writeText(url);
};
</script>

<style scoped>
.v-img:hover {
  cursor: pointer;
  filter: saturate(150%);
}

#image-card:hover {
  transition: all 0.5s;
  transform: scale(1.1);
}
</style>

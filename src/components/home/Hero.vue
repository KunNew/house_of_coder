<script setup>
import { useDisplay } from "vuetify/lib/framework.mjs";

const { mdAndUp } = useDisplay();
</script>
<template>
  <v-row align="center" class="flex-row-reverse">
    <v-col cols="12" sm="12" md="6">
      <v-img
        cover
        max-width="550px"
        class="mx-auto"
        src="/public/home-intro.svg"
      ></v-img>
    </v-col>
    <v-col cols="12" sm="12" md="6">
      <h1
        class="text-h4 text-sm-h4 text-md-h2 font-weight-bold"
        style="color: #5a96e3"
      >
        World Class Mobile Solutions
      </h1>
      <v-btn
        color="#0A6EBD"
        class="text-white rounded-lg mt-5 d-flex align-center font-weight-regular"
        flat
        :width="`${mdAndUp ? `` : `100%`}`"
        :size="mdAndUp ? `x-large` : `large`"
      >
        Get a Quote
      </v-btn>
    </v-col>
  </v-row>
</template>

<style soped></style>

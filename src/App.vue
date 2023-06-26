<template>
  <v-app class="grid-container">
    <navbar :color="color" :flat="flat" />
    <v-main>
      <transition name="page" mode="out-in">
        <router-view />
      </transition>
    </v-main>
    <v-scale-transition>
      <v-btn
        v-show="fab"
        class="ma-5"
        style="z-index: 999"
        position="fixed"
        location="bottom right"
        v-scroll="onScroll"
        icon="mdi-arrow-up"
        color="primary"
        @click="toTop()"
        size="large"
      >
      </v-btn>
    </v-scale-transition>
    <Footer />
  </v-app>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";

import { onMounted, ref, watch } from "vue";
const fab = ref(null);
const flat = ref(null);
const color = ref(null);

watch(fab, (value) => {
  if (value) {
    color.value = "#164B60";
    flat.value = false;
  } else {
    color.value = "transpaent";
    flat.value = true;
  }
});

const onScroll = (e) => {
  if (typeof window === "undefined") return;
  const top = window.pageYOffset || e.target.scrollTop || 0;
  fab.value = top > 60;
};
const toTop = () => {
  window.scroll({ top: 0, behavior: "smooth" });
};

onMounted(() => {
  const top = window.pageYOffset || 0;
  if (top <= 60) {
    color.value = "transparent";
    flat.value = true;
  }
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Belanosima:wght@400;600;700&display=swap");
.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}
</style>

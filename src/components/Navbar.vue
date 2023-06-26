<script setup>
import { onMounted, onUnmounted, watch } from "vue";
import { ref } from "vue";
const drawer = ref(false);
const isXs = ref(false);
const items = [
  ["fas fa-home", "ទំព័រដើម", "/"],
  ["fas fa-newspaper", "អត្ថបទ", "/blog"],
];
defineProps({
  flat: {
    type: Boolean,
  },
  color: {
    type: String,
  },
});
const onResize = () => {
  isXs.value = window.innerWidth < 850;
};

onMounted(() => {
  onResize();
  window.addEventListener("resize", onResize, { passive: true });
});

watch(isXs, (value) => {
  if (!value) {
    if (drawer.value) drawer.value = false;
  }
});

onUnmounted(() => {
  onResize();

  window.removeEventListener("resize", onResize);
});
</script>
<template>
  <v-navigation-drawer v-model="drawer" temporary>
    <v-list>
      <v-list-item>
        <v-responsive class="text-center">
          <v-avatar size="120" class="border pa-2">
            <v-img
              cover
              src="/public/house_of_coder.jpeg"
              max-width="120px"
              alt="logo"
            />
          </v-avatar>
        </v-responsive>
        <v-list-item-subtitle>
          <v-img src="/public/logo.svg" class="mx-auto" width="180px" />
        </v-list-item-subtitle>
      </v-list-item>
    </v-list>
    <v-divider></v-divider>
    <v-list nav>
      <v-list-item
        v-for="([icon, text, link], i) in items"
        :key="i"
        :to="link"
        exact
      >
        <div class="d-flex align-center">
          <v-list-item-action class="mr-3">
            <v-icon size="12" :class="icon"></v-icon>
          </v-list-item-action>
          <v-list-item-title>
            {{ text }}
          </v-list-item-title>
        </div>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
  <v-app-bar
    elevation="0"
    class="px-5 border-b"
    :flat="flat"
    :class="{ expand: flat }"
  >
    <v-toolbar-title>
      <router-link to="/">
        <v-img src="/logo.svg" :max-width="!isXs ? '200px' : '180px'"></v-img>
      </router-link>
    </v-toolbar-title>

    <v-app-bar-nav-icon
      @click="drawer = !drawer"
      v-if="isXs"
    ></v-app-bar-nav-icon>
    <template v-else>
      <v-btn text to="/" exact class="mr-2">
        <v-icon class="fas fa-home mr-2"></v-icon>
        <span> ទំព័រដើម </span>
      </v-btn>
      <v-btn text to="/blog" exact class="mr-2">
        <v-icon class="fas fa-newspaper mr-2"></v-icon>
        <span> អត្ថបទ</span>
      </v-btn>
    </template>
  </v-app-bar>
</template>

<style scoped>
.v-toolbar {
  transition: 0.6s;
}
.expand {
  height: 80px !important;
  padding-top: 10px;
}
.v-btn--active {
  background-color: #5a96e3;
  color: white;
  font-weight: bold;
}
.v-list-item--active {
  background-color: #5a96e3;
  color: white;
  font-weight: bold;
}
</style>

<script setup></script>
<template>
  <v-container class="pt-16">
    <v-row align="center px-5 py-5">
      <v-col cols="12" md="6">
        <h2 class="text-md-h2 text-h3 font-weight-bold mb-5">Blogs</h2>
        <p class="text-grey-darken-2 text-md-body-1 text-sm-body-2">
          Here you will find all the blog posts I have written & published on
          this site.
        </p>
      </v-col>
      <v-col cols="12" md="6">
        <v-img src="/undraw_wordpress_utxt.svg" width="100%"></v-img>
      </v-col>
    </v-row>
    <v-card border flat rounded="lg" class="overflow-hidden card" elevation="0">
      <v-row>
        <v-col cols="12" md="4">
          <v-img
            class="img"
            cover
            src="/blogs-img/vuejs.png"
            height="100%"
            style="object-position: center"
          />
        </v-col>
        <v-col cols="12" md="8" class="pa-6">
          <h2 class="text-h5 font-weight-bold">What is Vue?</h2>
          <p class="text-body-1">
            Vue (pronounced /vjuː/, like view) is a JavaScript framework for
            building user interfaces.
          </p>
          <div class="d-flex pt-5 mb-3 text-body-2 text-grey-darken-2">
            <div class="d-flex align-center mr-6">
              <v-icon class="fas fa-calendar mr-2" size="16"></v-icon>
              <span>18 june 2023</span>
            </div>
            <div class="d-flex flex-wrap">
              <v-card rounded border flat class="pa-1">
                <v-icon size="small" class="pr-1">mdi-tag</v-icon>
                <span>VUE</span>
              </v-card>
            </div>
          </div>
          <div class="pt-2">
            <router-link to="/blog-detail/123">
              <button class="btn-read-more">
                Read More
                <v-icon class="ml-2 fas fa-arrow-right"></v-icon>
              </button>
            </router-link>
          </div>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<style scoped>
.btn-read-more {
  background-color: #d91b42;
  padding: 4px 32px;
  color: white;
  font-weight: bold;
  border-radius: 4px;
  border: 0;
  text-decoration: none;
}
.btn-read-more:hover {
  transform: rotate(1.3deg);
}
.card .img {
  transition-duration: 0.2s;
}
.card .img:hover {
  transform: scale(1.05) !important;
}
</style>

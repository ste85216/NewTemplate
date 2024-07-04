<template>
  <v-navigation-drawer v-if="mobile" v-model="drawer">
    <v-list nav>
      <v-list-item v-for="item in navItems" :key="item.to" :to="item.to" :title="item.text"></v-list-item>
    </v-list>
  </v-navigation-drawer>

  <v-app-bar>
    <v-container class="d-flex align-center">
      <v-img id="logo" src="../assets/logo-volleycup.png" @click="goHome.to"></v-img>
      <v-spacer />
      <template v-if="mobile">
        <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
      </template>
      <template v-else>
        <v-btn v-for="item in navItems" :key="item.to" :to="item.to">{{ item.text }}</v-btn>
      </template>
    </v-container>
  </v-app-bar>
  <v-main>
    <swiper></swiper>
    <v-container>
      <sectionOne></sectionOne>
    </v-container>
  </v-main>
</template>

<script setup>
import { ref } from 'vue'
import { useDisplay } from 'vuetify'
import swiper from '../components/swiper.vue'
import sectionOne from '../components/sectionOne.vue'

const { mobile } = useDisplay()

const drawer = ref(false)

const goHome = { to: ''}

// 導覽列
const navItems = [
  { to: '/', text:"Home" }, 
  { to: '/aboutus', text:"About Us"}, 
  { to: '/trainings', text:"Trainings" }, 
  { to: '/packages', text:"Packages" }, 
  { to: '/blog', text:"Blog" }, 
  { to: '/contact', text:"Contact" }, 
]


</script>

<style scoped lang="scss">
:deep(.v-toolbar__content) {
  height: 120px !important;
}
#logo {
  height: 75px;
}
</style>

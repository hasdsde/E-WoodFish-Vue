<template>
  <q-layout view="hHh Lpr fFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <Aside />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue';
import Aside from 'src/components/Aside.vue';
import { menus } from 'src/components/models';
import { useRouter } from 'vue-router';
import { list } from 'postcss';
const $router = useRouter()
const leftDrawerOpen = ref(false)
let CurrentMemu = ref([])

function loadPage() {

}
loadPage()


function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
watch(() => $router.currentRoute.value.path, (oldValue, newValue) => {
  updateBreadcrumbs()
})
//面包屑
function updateBreadcrumbs() {
  menus.forEach((element: any) => {
    if (element.link == $router.currentRoute.value.path.replace('/', '')) {
      CurrentMemu.value = element
      console.log(CurrentMemu.value)
    }
  });
}
</script>
<style>
.body--dark {
  background: #000
}
</style>

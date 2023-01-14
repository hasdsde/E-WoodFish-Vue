<template>
  <div>
    <q-list padding class="rounded-borders text-primary">
      <q-item clickable v-ripple :active="link === item.link" v-for="(item, index) in menus" :key="index"
        @click="link = item.link" :to="item.link" active-class="my-menu-link">
        <q-item-section avatar>
          <q-icon :name="item.icon" />
        </q-item-section>
        <q-item-section>{{ item.desc }}</q-item-section>
      </q-item>
    </q-list>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { menus } from 'components/models.ts'
const link = ref('inboxs')

</script>

<style lang="css">
.my-menu-link {
  color: white;
  background: #F2C037
}
</style>

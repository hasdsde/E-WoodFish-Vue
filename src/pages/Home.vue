<template>
  <div class="q-pa-md  q-mt-xl">

    <div class="row">
      <div class="col">
      </div>
      <div class="col-6">
        <div class="woodFish">
          <q-img height="400px" ratio="1" fit="contain" src="../assets/woodfish_Black.png" alt="木鱼高清图" />
        </div>
      </div>
      <div class="col">
      </div>
    </div>
    <div class="animated bounce text-center">
      <q-btn color="primary" label="点击木鱼" @click="handleClick" />
    </div>
  </div>
  <div class="score_plus">
    <transition enter-active-class="animated backOutUp slower" leave-active-class="animated backOutUp slower">
      <q-btn size="lg" color="purple" v-if="show" label="功德+1" />
      <!-- <div v-if="show">功德+1</div> -->
    </transition>
  </div>

</template>
<script setup lang="ts">
import { ref } from 'vue';
const show = ref(false)

//点击事件
function handleClick() {
  show.value = true
  setTimeout(function () {
    show.value = false
  }, 1)
}

</script>

<style>
.score_plus {
  position: absolute;
  top: 200px;
  left: 60%;
}
</style>

<script setup lang="ts">
import AppNavBar from "./AppNavBar.vue";
import AppHeader from "./AppHeader.vue";
import BoardNavBar from "./BoardNavBar.vue";
import { computed } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const routeName = computed(() => route.name);
</script>
<template>
  <AppHeader />
  <div class="flex h-[93vh] pt-10">
    <AppNavBar v-if="routeName !== 'board-id'" />
    <BoardNavBar v-else />
    <section class="overflow-x-auto ml-10 min-w-full">
      <transition>
        <RouterView />
      </transition>
    </section>
  </div>
</template>

<style>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>

<script lang="ts" setup>
import { Card, CardTitle } from "@progress/kendo-vue-layout";
import type { Board } from "@/types";
import { defineProps } from "vue";

const props = defineProps<{
  board: Board;
}>();

const randomColor = "#" + Math.floor(Math.random() * 16777215).toString(16);
</script>

<template>
  <RouterLink :to="`/board/${board.id}`">
    <Card class="relative h-40 w-60 bg-[#091e420a]">
      <div v-if="board?.image">
        <img
          class="w-full h-full"
          :src="board.image.downloadUrl"
          alt="BoardImage"
        />
      </div>
      <div
        v-else
        class="h-full w-full"
        :style="{ background: randomColor }"
      ></div>
      <CardTitle class="absolute top-2 left-2 leading-4 text-white bold">{{
        board.title
      }}</CardTitle>
    </Card>
  </RouterLink>
</template>

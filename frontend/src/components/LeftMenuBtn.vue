<script setup lang="ts">
import type { FunctionalComponent } from "vue";

defineProps<{
  title: string;
  textStyle?: any;
  icon?: FunctionalComponent;
  isActive?: boolean;
}>();
</script>

<template>
  <div :class="{ btn: true, isActive: isActive }">
    <component :is="icon" v-if="icon"></component>
    <a-typography-text class="text ml-6" :style="textStyle">
      {{ title }}
    </a-typography-text>
  </div>
</template>

<style lang="scss" scoped>
.isActive {
  background-color: #45475a;
  color: #89b4fa !important;
}
.btn {
  display: flex;
  text-align: center;
  display: flex;
  align-items: center;
  height: 40px;
  padding: 0px 12px;
  min-width: 40px;
  cursor: pointer;
  border-radius: 6px;
  transition: all 0.2s;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  width: 100%;

  .text {
    overflow: hidden;
    text-overflow: ellipsis;
    color: #cdd6f4;
  }

  &:hover {
    // background-color: var(--color-gray-5);
    background-color: #585b70;
  }
}
</style>

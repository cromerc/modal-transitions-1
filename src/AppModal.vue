<script setup>
import { XMarkIcon } from "@heroicons/vue/20/solid";
defineProps({
  title: { type: String, default: null },
  show: { type: Boolean, default: false },
});

defineEmits(["close"]);
</script>

<template>
  <Transition>
    <div class="modal-wrapper" v-if="show">
      <div class="modal-wrapper-inner">
        <button class="modal-close-button" @click="$emit('close')">
          <XMarkIcon class="w-8 h-8" />
        </button>
        <h3 class="modal-title" v-if="title">{{ title }}</h3>
        <div class="modal-inner">
          <slot />
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.v-enter-from {
  transition: opacity 0.5s ease;
  opacity: 0;
}

.v-enter-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.v-enter-to {
  transform: translateY(50px);
  opacity: 1;
}

.v-leave-from {
  transition: opacity 0.5s ease;
  opacity: 1;
}

.v-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.v-leave-to {
  transform: translateY(-50px);
  opacity: 0;
}
</style>

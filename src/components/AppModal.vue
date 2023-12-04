<script setup>
import { XMarkIcon } from "@heroicons/vue/20/solid";
defineProps({
  title: { type: String, default: null },
  show: { type: Boolean, default: false },
});

defineEmits(["close"]);
</script>

<template>
  <div>
    <Transition>
      <div v-if="show" class="modal-wrapper">
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
  </div>
</template>

<style scoped>

.modal-wrapper {
    @apply absolute inset-0 flex items-center justify-center z-20 bg-gray-800/40 backdrop-blur;
}

.modal-close-button {
    @apply absolute -right-12 -top-2 text-gray-300 p-2 hover:text-white
}

.modal-title {
    @apply w-full bg-gray-900 p-4 rounded-t-md text-2xl
}

.modal-wrapper-inner {
    @apply relative shrink-0 w-full max-w-2xl rounded-md flex flex-col shadow-2xl bg-white dark:bg-gray-800 dark:text-white;
}

.modal-inner {
    @apply p-4 space-y-4
}

.v-enter-active,
.v-leave-active,
.v-enter-active .modal-wrapper-inner,
.v-leave-active .modal-wrapper-inner {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.v-enter-from .modal-wrapper-inner,
.v-leave-to .modal-wrapper-inner {
  transform: translateY(-50px);
}
</style>
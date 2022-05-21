<template>
  <div class="bg-yellow-200 border-yellow-600 text-yellow-600 border-l-4 p-4 notice-card" v-if="show">
      <p class="font-bold">
        {{ title }}
      </p>
      <p>
        {{ info }}
      </p>
  </div>
</template>

<script lang="ts">
import { defineComponent, toRef, Ref } from 'vue'

export default defineComponent({
  props: ['title', 'info', 'show'],
  setup(props) {
    const title: Ref<string> = toRef(props, 'title');
    const info: Ref<string> = toRef(props, 'info');
    const show: Ref<boolean> = toRef(props, 'show');
    return {
      title, info, show
    }
  },
})
</script>


<style lang="scss" scoped>
  @keyframes slideIn {
    0% {
      right: -30rem;
      display: block;
    }
    50% {
      right: 1rem;
    }
    to {
      display: none;
    }
  }
  .notice-card {
    position: absolute;
    right: 1rem;
    top: 4rem;
    width: 25rem;
    animation: slideIn 1s ease;
  }
</style>
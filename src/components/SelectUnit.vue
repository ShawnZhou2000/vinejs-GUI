<template>
  <div class="select-unit">
    <div class="shadow-lg rounded-2xl w-64 h-48 p-4 bg-white relative overflow-hidden mr-8"
      v-for="(item, index) in data" :key="index" @click="selectTarget(item.name, item.available)"
      :class="{ 
        'unit-active': item.available,
        'unit-disabled': !item.available,
        'unit-select': select === item.name
      }">
      <img
        src="/favicon.png"
        class="absolute mb-4 card-img"
      />
      <div class="w-5/6 select-main">
        <p class="text-gray-800 text-lg font-medium mb-4">{{ item.name }}</p>
        <p class="text-gray-400 text-sm font-normal mb-5">
          {{ item.intro }}
        </p>
        <p class="text-green-500 text-sm font-medium" v-if="item.available">更新时间：{{ item.time }}</p>
        <p class="text-red-500 text-sm font-medium" v-else>暂不可用</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, toRef } from "vue";

export default defineComponent({
  props: ['data', 'select'],
  setup(props, ctx) {
    const data = toRef(props, 'data');
    const select = toRef(props, 'select');
    const selectTarget = (name: string, check: boolean) => {
      if (check)
        ctx.emit('changeSelect', name);
    }
    return {
      data,
      selectTarget,
      select
    }
  },
});
</script>

<style lang="scss" scoped>
  .card-img {
    width: 8rem;
    right: -55px;
    top: -32px;
    transform: rotate(40deg);
    z-index: 0;
  }

  .select-unit {
    display: flex;
  }

  .select-main {
    position: relative;
    z-index: 1;
  }
  
  .unit-disabled {
    img {
      filter: grayscale(1);
    }
  }

  .unit-select {
    border: 2px solid #10B981;
  }

  .unit-active {
    border: 2px solid transparent;
    transition: all 0.1s ease;
  }
  .unit-active:hover {
    cursor: pointer;
    border: 2px solid #10B981;
  }
</style>

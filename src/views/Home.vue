<template>
  <div class="bg-gray-50">
    <div
      class="mx-auto max-w-screen-xl px-4 py-12 sm:px-6 lg:flex lg:justify-between lg:py-16 lg:px-8 flex flex-col"
    >
      <h2
        class="text-3xl font-normal leading-9 tracking-tight text-gray-900 sm:text-4xl sm:leading-10"
      >
        欢迎使用 Vine.js 图形控制面板
        <br />
        <span class="text-green-600 text-2xl letter-1"
          >在以下栏目中选择一项以开始</span
        >
      </h2>
      <div class="flex flex-row justify-evenly mt-10">
        <HomeSelect 
        v-for="(item, index) in indexList" 
        :key="index" :title="item.title"
        :description="item.description"
        :icon="item.icon" :mode="item.mode"
        @clickCard="handleClickCard(item.mode)"
        ></HomeSelect>
      </div>
      <Notice :show="WIP.show" :title="WIP.title" :info="WIP.info"></Notice>
      <CreateCard :show="createShow" @cancel="cancel"></CreateCard>
    </div>
  </div>
</template>

<script setup>
import HomeSelect from '@/components/HomeSelect.vue';
import Notice from  '@/components/Notice.vue';
import CreateCard from  '@/components/CreateCard.vue';
import { ref, reactive } from '@vue/reactivity';

let createShow = ref(false);
let openShow = ref(false);

const cancel = () => {
  createShow.value = false;
  openShow.value = false;
}

const WIP = reactive({
  title: 'Still Work in Progress',
  info: '此功能还在开发中',
  show: false,
})

const indexList = [
  {
    title: '创建新项目',
    description: '使用 Vine.js 为你创建一个全新的 Web 应用，快速搭建个人网站，在本地修改、调试，并使用部署器发布上线。',
    icon: 'icon-create',
    mode: 'create'
  },
  {
    title: '打开已有项目',
    description: '选择一个已经创建好的 Vine.js 项目，继续维护你的网站，为网站添加扩展件，修改部署器配置等。',
    icon: 'icon-open',
    mode: 'open'
    
  },
  {
    title: '升级 Guider 版本',
    description: '自动更新 Guider 到最新版本，获取最新 Vine.js Guider 功能，解决已有问题。',
    icon: 'icon-update',
    mode: 'update'
  }
]

const handleClickCard = (mode) => {
  switch (mode) {
    case 'create':
      createShow.value = true;
      break;
    case 'open':
      openShow.value = true;
      break;
    case 'update':
      WIP.show = true;
      setTimeout(() => {
        WIP.show = false;
      }, 1000);
      break;
  }
}

</script>

<style lang="scss" scoped>
.letter-1 {
  letter-spacing: 1px;
}
</style>

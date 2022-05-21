<template>
  <div class="create-card">
    <div class="relative">
      <div class="h-screen w-full z-10 inset-0 overflow-y-auto">
        <div
          class="absolute w-full h-full inset-0 bg-gray-500 opacity-75"
        ></div>
        <div
          class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0 card-outer"
        >
          <div
            class="inline-block relative overflow-hidden transform transition-all card-main"
          >
            <div>
              <div class="rounded-lg p-8 bg-white shadow">
                <div class="bg-white dark:bg-gray-800">
                  <div
                    class="text-left w-full mx-auto px-4 sm:px-6 lg:py-8 lg:px-8 z-20"
                  >
                    <h2
                      class="font-extrabold text-black dark:text-white"
                    >
                      <div class="create-unit">
                        <span class="block text-3xl"> 工作区 </span>
                        <SelectWorkSpace></SelectWorkSpace>
                      </div>
                      <div class="create-unit">
                        <span class="block text-3xl"> 主核心 </span>
                        <SelectUnit :data="coreList"></SelectUnit>
                      </div>
                      <div class="create-unit">
                        <span class="block text-3xl"> 部署器 </span>
                        <SelectUnit :data="deployerList"></SelectUnit>
                      </div>
                    </h2>
                    <div
                      class="flex items-center justify-between gap-4 w-1/4 mt-8 btn-panel"
                    >
                      <button
                        type="button"
                        class="py-2 px-4 bg-green-600 hover:bg-green-700 focus:ring-green-500 focus:ring-offset-green-200 text-white transition ease-in duration-200 text-center text-base font-normal shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2 rounded-lg"
                      >
                        新建
                      </button>
                      <button
                        type="button"
                        class="py-2 px-4 bg-white hover:bg-gray-100 focus:ring-green-500 focus:ring-offset-green-200 text-green-500 transition ease-in duration-200 text-center text-base font-normal shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2 rounded-lg"
                      >
                        取消
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SelectUnit from "./SelectUnit.vue";
import SelectWorkSpace from "./SelectWorkSpace.vue";

export default defineComponent({
  components: {
    SelectUnit,
    SelectWorkSpace
},
  setup() {
    const coreList = [
      {
        name: 'Blog Core',
        intro: '个人博客主核心，用于快速搭建静态博客站点，专注于你的写作，使用 Markdown 编写文章并发布。',
        time: '2022/5/21',
        available: true,
      },
      {
        name: 'H5 Core',
        intro: 'HTML5 移动端展示主核心，快速生成电子海报、节日贺卡、生日祝福、活动推广页的首选。',
        time: '2022/5/21',
        available: false,
      },
      {
        name: 'Note Core',
        intro: '云端笔记主核心，以电子书形式呈现，打造你的个人远程知识库，支持 Markdown 或富文本编辑器进行写作。',
        time: '2022/5/21',
        available: false,
      },
      {
        name: 'Gallery Core',
        intro: '云端相册主核心，通过照片记录生活的美好瞬间，使用时需连接 Vine 支持的图床服务。',
        time: '2022/5/21',
        available: false,
      }
    ];

    const deployerList = [
      {
        name: 'Git Deployer',
        intro: '通过 Git 版本管理工具部署到静态网站托管服务，如 Vercel 或 GitHub Pages。',
        time: '2022/5/5',
        available: true,
      },
      {
        name: 'Aliyun OSS Deployer',
        intro: '将静态网站上传至阿里云 OSS 静态对象存储服务。',
        time: '2022/5/5',
        available: true,
      },
      {
        name: 'Aliyun Server Deployer',
        intro: '通过 SSH 连接，将静态网站上传至阿里云服务器主机。',
        time: '2022/5/5',
        available: false,
      },
      {
        name: 'Tencent Cloudbase Deployer',
        intro: '将静态网站上传至腾讯云 Cloudbase 服务。',
        time: '2022/5/5',
        available: false,
      }
    ];

    return {
      coreList,
      deployerList
    }
  },
});
</script>

<style lang="scss" scoped>
.create-card {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

.card-main {
  width: 50%;
}

.btn-panel {
  margin: 3rem auto 0;
  button {
    width: 10rem;
  }
}

.create-unit {
  margin-bottom: 4rem;
  span {
    margin-bottom: 3rem;
  }
}

.card-outer {
  display: flex;

}
</style>
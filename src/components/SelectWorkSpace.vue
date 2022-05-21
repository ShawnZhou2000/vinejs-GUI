<template>
  <div>
    <div
      class="rounded-md flex items-center jusitfy-between px-5 py-4 mb-2 border border-green-500 text-green-500"
    >
      <div class="flex items-center w-full">
        <img src="/folder.svg" />
        <div class="project-name ml-4">
          <div class="relative">
            <input
              type="text"
              v-model="workspace"
              id="workspace"
              class="border-transparent flex-1 w-full py-2 bg-white text-green-500 placeholder-green-500 text-base focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-transparent"
              placeholder="输入工作区路径"
            />
          </div>
        </div>
      </div>
    </div>
    <div
      class="rounded-md flex items-center jusitfy-between px-5 py-4 mb-2 border border-green-500 text-green-500"
    >
      <div class="flex items-center w-full">
        <img src="/tag.svg" />
        <div class="project-name ml-4">
          <div class="relative">
            <input
              type="text"
              v-model="projectName"
              id="project-name"
              class="border-transparent flex-1 w-full py-2 bg-white text-green-500 placeholder-green-500 text-base focus:outline-none focus:ring-2 focus:ring-green-600 focus:border-transparent"
              placeholder="输入项目名"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    let workspace = ref('');
    let projectName = ref('');
    return {
      workspace,
      projectName,
    };
  },
});
</script>

<style lang="scss" scoped>
.hidden-form {
  display: none;
}

.project-name {
  input {
    padding: 6px 0;
  }
}
</style>

<template>
  <div class="container flex flex-row align-super justify-center">
    <div class="orbment-main w-full">
      <OrbmentBase></OrbmentBase>
    </div>
  </div>
</template>

<script setup>
  import OrbmentBase from '../components/Orbment/OrbmentBase.vue';
</script>

<style lang="scss" scoped>
  .container {
    margin: 0 auto;
    min-height: 865px;
  }

  .orbment-main {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .orbment-side {
    border: 1px solid green;
  }
</style>
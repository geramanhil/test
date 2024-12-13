<script setup>
  import leftBlocks from './components/leftBlocks.vue';
  import rightBlocks from './components/rightBlocks.vue';
</script>

<template>
  <div class="container">
    <leftBlocks/>
    <rightBlocks/>
  </div>
</template>

<style lang="scss" scoped>
.container{
  display: flex;
  column-gap: 10px;
}
</style>

<script setup>
// import HelloWorld from './components/HelloWorld.vue';
import ProductSelectorCompApi from './components/ProductSelectorCompApi.vue';
import ProductsSelector from './components/ProductsSelector.vue';
// import SimpleComposition from './components/SimpleComposition.vue';
</script>

<template>
  <!-- <HelloWorld /> -->
  <div class="container">
    <ProductsSelector />
    <ProductSelectorCompApi />
  </div>
  <!-- <SimpleComposition :initial-count="10" @increment="console.log('I was increment', $event)"/> -->
</template>

<style>
.container {
  padding: 1rem;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}
</style>

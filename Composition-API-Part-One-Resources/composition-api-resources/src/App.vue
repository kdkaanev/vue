<script>
// import HelloWorld from './components/HelloWorld.vue';
// import ProductsSelector from './components/ProductsSelector.vue';
import SimpleComposition from './components/SimpleComposition.vue';

export default {
  components: {
    // HelloWorld,
    // ProductsSelector,
    SimpleComposition,
  },
};
</script>

<template>
  <!-- <HelloWorld />
  <ProductsSelector /> -->
  <SimpleComposition :initial-count="10" @increment="console.log('I was increment', $event)"/>
</template>

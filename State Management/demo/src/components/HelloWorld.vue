<script>
import { mapActions, mapState } from 'pinia';
import { useCountStore } from '../stores/useCountStore';

export default {
  // setup() {
  //   return {
  //     countStore: useCountStore(),
  //   };
  // },
  computed: {
    ...mapState(useCountStore, ['count', 'doubleCount']),
  },
  methods: {
    ...mapActions(useCountStore, ['increment']),
  },
};
</script>

<template>
  <div class="container" style="text-align:center">
    <img src="../assets/vue.svg" alt="Logo" style="width: 10rem; margin: 1rem auto;">
    <h1>{{ msg }}</h1>

    <div class="card">
      <!-- <button type="button" @click="countStore.increment">
        count is {{ countStore.count }}
      </button>
      <h1> double count is {{ countStore.doubleCount }}</h1> -->

      <button type="button" @click="increment">
        count is {{ count }}
      </button>
      <h1> double count is {{ doubleCount }}</h1>
      <p>
        Edit
        <code>components/HelloWorld.vue</code> to test HMR
      </p>
    </div>

    <p>
      Check out
      <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
      starter
    </p>
    <p>
      Install
      <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
      in your IDE for a better DX
    </p>
    <p class="read-the-docs">
      Click on the Vite and Vue logos to learn more
    </p>
  </div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>

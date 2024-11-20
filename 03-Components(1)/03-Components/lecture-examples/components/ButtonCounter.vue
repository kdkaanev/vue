<script>
export default {
  props: {
    text: String,
    title: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    onClick() {
      this.count += 1;
    },
  },
};
</script>

<template>
  <button @click="onClick">
    {{ text }} {{ count }}
  </button>
</template>

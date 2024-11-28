<script>
export default {
  data() {
    return {
      textValue: 'test',
      title: 'Example title',
    };
  },
  methods: {
    onInput(event) {
      this.textValue = event.target.value;
    },
  },
};
</script>

<template>
  <input type="text" :value="textValue" @input="onInput">
  <p>My Text is {{ textValue }}</p>

  <input type="text" :value="title" @input="onInput">
  <p>My Text is {{ title }}</p>
</template>

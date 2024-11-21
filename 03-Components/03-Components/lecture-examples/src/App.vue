<script>
import ButtonCounter from '../components/ButtonCounter.vue';

export default {
  components: {
    ButtonCounter,
  },
  data() {
    return {
      customText: 'custom text',
    };
  },
};
</script>

<template>
  <h1>Components examples</h1>
  <ButtonCounter title="Some title" text="I was clicked x: " />
  <ButtonCounter text="1234" disabled />
</template>

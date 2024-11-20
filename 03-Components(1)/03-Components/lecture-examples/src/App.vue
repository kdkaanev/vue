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
  <ButtonCounter title="some title" text="I was clicked x: " />
  <ButtonCounter title="some title" :text="customText" />
  <ButtonCounter title="some title" text="1" />
</template>

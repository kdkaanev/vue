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
  <ButtonCounter title-text="Some title" text="I was clicked x: " @was-incremented="(arg) => console.log('wasIncremented')" />
  <ButtonCounter text="1234" disabled />
</template>

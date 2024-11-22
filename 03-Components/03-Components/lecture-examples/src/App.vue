<script>
import AcceptButton from '../components/AcceptButton.vue';
import ButtonCounter from '../components/ButtonCounter.vue';
import DeclineButton from '../components/DeclineButton.vue';
import Layout from '../components/Layout.vue';

export default {
  components: {
    ButtonCounter,
    AcceptButton,
    DeclineButton,
    Layout,
  },
  data() {
    return {
      customText: 'custom text',
      wasAccepted: false,
    };
  },
};
</script>

<template>
  <h1>Components examples</h1>
  <ButtonCounter
    title-text="Some title"
    text="I was clicked x: " @was-incremented="(arg) => console.log('wasIncremented')"
  />
  <ButtonCounter text="1234" disabled />

  <br>
  <br>
  <ButtonCounter
    text="make it toogle"
    @was-incremented="wasAccepted = !wasAccepted"
  />

  <component :is="wasAccepted ? 'AcceptButton' : 'DeclineButton'" />

  <Layout>
    <template #footer>
      New
    </template>
  </Layout>
</template>

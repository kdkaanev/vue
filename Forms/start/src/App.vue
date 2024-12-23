<script>
import AppInput from './components/AppInput.vue';
import AppNamesInput from './components/AppNamesInput.vue';
import BasicExample from './components/BasicExample.vue';
import RegistrationForm from './components/RegistrationForm.vue';

export default {
  components: {
    RegistrationForm,
    BasicExample,
    AppInput,
    AppNamesInput,
  },
  data() {
    return {
      customText: '',
      fName: 'Kancho',
      lName: 'Kaanev',
    };
  },

};
</script>

<template>
  <RegistrationForm />
  <BasicExample />

  <AppInput id="example1" v-model="customText" placeholder="Write someting" name="My custom component" />
  <p>Example: {{ customText }}</p>
  <AppNamesInput v-model:first-name="fName" v-model:last-name="lName" />
  <p>My name is: {{ fName }} {{ lName }}</p>
</template>

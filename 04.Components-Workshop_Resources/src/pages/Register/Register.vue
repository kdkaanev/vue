<script>
import AddressForm from './components/AddressForm.vue';
import GeneralForm from './components/GeneralForm.vue';

export default {
  components: {
    GeneralForm,
    AddressForm,
  },
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      userInformation: {
        name: '',
        password: '',
        confirmPassword: '',
        email: '',
        phone: '',
        gender: '',
        payment: '',
        note: '',

      },
      activeStep: 'general',
    };
  },
  methods: {
    onNextStep(generalData) {
      this.userInformation = {
        ...this.userInformation,
        ...generalData,
      };
      this.goNext();
    },
    goNext() {
      this.activeStep = 'address';
    },
    goPrevious() {
      this.activeStep = 'general';
    },
    onSubmit(generalData) {
      this.userInformation = {
        ...this.userInformation,
        ...generalData,
      };
      console.log('I WAS FINALLY SUBMITED', this.userInformation);
    },
  },
};
</script>

<template>
  <section>
    <article>
      <header>
        <h1>
          {{ activeStep === 'general' ? 'Step 1: General Information' : 'Step 2: Address Information' }}
        </h1>
      </header>
      <GeneralForm v-if="activeStep === 'general'" :data="userInformation" @next="onNextStep" />
      <AddressForm v-else :data="userInformation" @previous="goPrevious" @submit="onSubmit" />
    </article>
  </section>
</template>

<style scoped>
section{
  padding:1rem;
}
article{
  max-width: 800px;
  margin: auto;
}
</style>

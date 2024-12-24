<script>
import useVuelidate from '@vuelidate/core';
import { maxLength, required } from '@vuelidate/validators';
import DoubleRow from './DoubleRow.vue';
import FormFieldSet from './FormFieldSet.vue';

export default {
  components: {
    FormFieldSet,
    DoubleRow,
  },
  emits: ['previous', 'submit'],
  setup() {
    return {
      v$: useVuelidate(),
    };
  },
  data() {
    return {
      formData: {
        address1: '',
        address2: '',
        city: '',
        ZIP: null,
        country: '',
        payment: '',
        note: '',
      },
    };
  },

  validations() {
    return {
      formData: {
        address1: {
          required,
          minLength: maxLength(5),
        },
      },
    };
  },
  methods: {
    async onSubmit() {
      const isValid = await this.v$.$validate();
      if (isValid) {
        this.$emit('submit', this.formData);
      }
    },
  },
};
</script>

<template>
  <form @submit.prevent="onSubmit">
    <FormFieldSet title="Address line 1" :errors="v$.formData.address1.$errors">
      <input
        v-model="v$.formData.address1.$model" type="text" placeholder="Jane Doe ..." @blur="v$.formData.name.$touch"
      >
    </FormFieldSet>
    <FormFieldSet title="Address line 2" :errors="[]">
      <input
        v-model="formData.address2" type="text" placeholder="Jane Doe ..."
      >
    </FormFieldSet>

    <DoubleRow>
      <button type="button" class="secondary" @click="$emit('previous')">
        Previous
      </button>
      <button type="submit" class="primary">
        Submit
      </button>
    </DoubleRow>
  </form>
</template>

<style scoped>
form {
    display: grid;
    gap: 1rem;
}
input, select{
  margin: 0;
}
</style>

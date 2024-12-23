<script>
import DoubleRow from './DoubleRow.vue';
import FormFieldSet from './FormFieldSet.vue';

export default {
  compoments: {
    FormFieldSet,
    DoubleRow,
  },
};
</script>

<template>
  <form>
    <FormFieldSet title="Name">
      <input
        type="text" placeholder="Jane Doe ..."
      >
    </FormFieldSet>
    <DoubleRow>
      <FormFieldSet title="Password">
        <input
          type="password" placeholder="Strong password ..."
        >
      </FormFieldSet>
      <FormFieldSet title="Comfirm">
        <input
          type="password" placeholder="Comfirm password ..."
        >
      </FormFieldSet>
    </DoubleRow>

    <DoubleRow>
      <FormFieldSet title="Email">
        <input
          type="email" placeholder="janedow@gmail.com ..."
        >
      </FormFieldSet>
      <FormFieldSet title="Phone Number">
        <input
          type="text" placeholder="359 999 999 ..."
        >
      </FormFieldSet>
    </DoubleRow>

    <DoubleRow>
      <FormFieldSet title="Gender">
        <select>
          <option value="">
            Select gender
          </option>
          <option value="male">
            Male
          </option>
          <option value="female">
            Female
          </option>
          <option value="other">
            Other
          </option>
        </select>
      </FormFieldSet>
      <FormFieldSet title="Date of Birth">
        <input
          type="date" placeholder="dd/mm/yyyy ..."
        >
      </FormFieldSet>
    </DoubleRow>
  </form>
</template>

<style>
form {
    display: grid;
    gap: 1rem;
}
</style>

<script>
export default {
  props: {
    firstName: {
      type: String,
      required: true,
    },
    lastName: {
      type: String,
      required: true,
    },
  },
  emits: [
    'update:firstName',
    'update:lastName',
  ],
};
</script>

<template>
  <fieldset>
    <label for="id">firstName</label>
    <input id="firstName" type="text" :value="firstName" @input="$emit('update:firstName', $event.target.value)">
  </fieldset>
  <fieldset>
    <label for="id">lastName</label>
    <input id="lastName" type="text" :value="lastName" @input="$emit('update:lastName', $event.target.value)">
  </fieldset>
</template>

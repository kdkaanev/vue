<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      message: '',
      frameworks: [],
      acceptedTerms: 'Accept',
      car: '',
      isSelected: false,
      wasToggled: 'yes',
    };
  },
  methods: {
    onInput(event) {
      this.firstName = event.target.value;
    },
  },
};
</script>

<template>
  <article>
    <header>
      Leave your feedback
    </header>
    <input type="text" :value="firstName" @input="onInput">
    <p>My First Name: {{ firstName }}</p>

    <input v-model="lastName" type="text">
    <p>My Last Name {{ lastName }}</p>

    <textarea v-model="message" placeholder="Write me a message" />
    <p>My Message : {{ message }}</p>

    <fieldset>
      <p>Select your JS framework</p>
      <label>
        <input v-model="frameworks" type="checkbox" value="vue">
        Vue
      </label>
      <label>
        <input v-model="frameworks" type="checkbox" value="txd">
        React
      </label>
      <label>
        <input v-model="frameworks" type="checkbox" value="ng">
        Angular
      </label>
      <p>Selected :{{ JSON.stringify(frameworks) }}</p>
    </fieldset>

    <fieldset>
      Accept the website terms!
      <label>
        <input v-model="acceptedTerms" type="radio" value="Accept"> Accept
      </label>
      <label>
        <input v-model="acceptedTerms" type="radio" value="Decline"> Decline
      </label>
      <p>Accepted value is: {{ acceptedTerms }}</p>
    </fieldset>
    <fieldset>
      <select v-model="car">
        <option disabled value="">
          Please select one
        </option>
        <option>Oplel</option>
        <option>Ferrary</option>
        <option>Mercedes</option>
      </select>
      <p>My car is: {{ car }}</p>
    </fieldset>
    <fieldset>
      <label for="">
        <input v-model="wasToggled" type="checkbox" true-value="yes" false-value="no">
        Was I Toggle? <span>{{ wasToggled }}</span>
      </label>
    </fieldset>
    <fieldset>
      <label for="">
        <input v-model="isSelected" type="checkbox" value="true">
        Was I Selected? <span>{{ isSelected }}</span>
      </label>
    </fieldset>
  </article>
</template>

<style scoped>
article {
  max-width: 500px;
  margin: 4rem auto 0;
}

fieldset {
  border: 1px coral solid;
}
</style>

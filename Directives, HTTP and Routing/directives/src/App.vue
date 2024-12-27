<script>
const focusDirectiveLogic = {

  mounted: (el, bindingdata) => {
    console.log('MAUNTED', el, bindingdata);
    if (bindingdata.value) {
      el.focus();
    }
  },
  updated: (el, bindingdata) => {
    console.log('UPDATED', el, bindingdata);
    if (bindingdata.value) {
      el.focus();
    }
  },
};

const colorDir = {
  mounted: (el, binding) => {
    if (binding.arg === 'background') {
      el.style.backgroundColor = binding.value;
    }
    else {
      el.style.color = binding.value;
    }
  },

};

export default {
  directives: {
    color: colorDir,
    focus: focusDirectiveLogic,
  },
  data() {
    return {
      shouldFokus: true,
    };
  },
};
</script>

<template>
  <button @click="shouldFokus = !shouldFokus">
    Toggle {{ shouldFokus }}
  </button>
  <input v-focus="shouldFokus">

  <p v-color="'red'">
    I'm using v-color whit text
  </p>
  <p v-color:background="'green'">
    I'm using v-color whit background
  </p>
</template>

<script>
export default {
  props: {
    title: {
      type: [String, Number],
      default: 'Default title',
    },
    text: {
      type: String,
      required: true,
      validator(propsValue) {
        return propsValue.length > 2;
      },
    },
    disabled: Boolean,
  },
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    onClick() {
      this.count += 1;
    },
  },
};
</script>

<template>
  <div>
    <h2>{{ title }}</h2>
    <button :disabled="disabled" @click="onClick">
      {{ text }} {{ count }}
    </button>
  </div>
</template>

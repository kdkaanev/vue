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
  emits: ['wasIncremented'],
  data() {
    return {
      count: 0,
    };
  },
  beforeCreate() {
    console.log('I was before created', this.count, this.text);
  },
  created() {
    console.log('I was created', this.count, this.text);
  },

  mounted() {
    console.log('I was mounted', this.count, this.text);
  },
  beforeUpdate() {
    console.log('I was before update', this.count, this.text);
  },
  updated() {
    console.log('I was update', this.count, this.text);
  },
  methods: {
    onClick() {
      this.count += 1;
      this.$emit('wasIncremented', this.count);
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

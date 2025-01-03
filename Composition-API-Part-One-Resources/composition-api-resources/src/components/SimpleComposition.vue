<script setup>
import { computed, reactive, ref, watch } from 'vue';

const props = defineProps({
  initialCount: {
    type: Number,
    requered: false,
    default: 0,
  },
});

const emit = defineEmits(['increment']);

const countState = ref(props.initialCount);
console.log('countState', countState);
function incrementCount() {
  countState.value += 1;
  emit('increment', countState.value);
}

const doubleCount = computed(() => countState.value * 2);

watch(countState, (newValue, oldValue) => {
  console.log('🎄WATCHER🎄', newValue, oldValue);
});

const deepStateRef = ref({
  lets: {
    have: {
      very: {
        nested: {
          number: {
            here: 0,
          },
        },
      },
    },
  },
});

const deepStateReactive = reactive({
  lets: {
    have: {
      very: {
        nested: {
          number: {
            here: 0,
          },
        },
      },
    },
  },
});

watch(() => deepStateRef.value.lets.have.very.nested.number.here, (newValue, oldValue) => {
  console.log('WATCHER', newValue, oldValue);
}, { deep: true });
function doSomethingWhitState() {
  const { number } = deepStateRef.value.lets.have.very.nested;
  number.here += 1;
  // deepStateReactive.lets.have.very.nested.number.here = 20;
  const { number: nReactive } = deepStateReactive.lets.have.very.nested;
  nReactive.here = 200;
}
</script>

<template>
  <h1>
    COMPOSITION API
  </h1>
  <button type="button" class="outline" @click="incrementCount">
    Example {{ countState }} | Double: {{ doubleCount }}
  </button>
  <h2>Deep & reactive examples</h2>
  <h3>REF: {{ deepStateRef.lets.have.very.nested.number.here }}</h3>
  <h3>reactive: {{ deepStateReactive.lets.have.very.nested.number.here }}</h3>
  <button @click="doSomethingWhitState">
    Do something
  </button>
</template>

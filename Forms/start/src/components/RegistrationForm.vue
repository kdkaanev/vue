<script>
import { useVuelidate } from '@vuelidate/core';
import { email, maxValue, minValue, required } from '@vuelidate/validators';

const SKILS = [
  {
    id: 'vue',
    name: 'VueJS',
  },
  {
    id: 'react',
    name: 'ReactJs',
  },
  {
    id: 'angular',
    name: 'Angular',
  },
  {
    id: 'js',
    name: 'JavaScript',
  },
  {
    id: 'ts',
    name: 'TypeScript',
  },
  {
    id: 'css',
    name: 'CSS',
  },
  {
    id: 'scss',
    name: 'SCSS',
  },
  {
    id: 'py',
    name: 'Python',
  },
  {
    id: 'go',
    name: 'Go',
  },
];
const COUNTRIES = [
  { id: 'bg', name: 'Bulgaria' },
  { id: 'us', name: 'United States' },
  { id: 'ca', name: 'Canada' },
  { id: 'de', name: 'Germany' },
  { id: 'fr', name: 'France' },
  { id: 'jp', name: 'Japan' },
  { id: 'au', name: 'Australia' },
  { id: 'br', name: 'Brazil' },
  { id: 'in', name: 'India' },
  { id: 'za', name: 'South Africa' },
];

export default {
  setup() {
    return {
      v$: useVuelidate(),
    };
  },
  data() {
    return {
      data: {
        firstName: '',
        lastName: '',
        email: '',
        age: 0,
        skillSet: [],
        gender: '',
        country: '',

      },
      skilsOptions: SKILS,
      countryOptions: COUNTRIES,
      isSubmited: false,
    };
  },
  validations() {
    return {
      data: {
        firstName: { required },
        lastName: { required },
        email: { required, email },
        age: {
          minValue: minValue(1),
          maxValue: maxValue(100),
        },
      },
    };
  },
  methods: {
    async onSubmit() {
      const isValid = await this.v$.$validate();
      if (isValid) {
        this.isSubmited = true;
      }
    },
  },
};
</script>

<template>
  <section class="pageSection">
    <article>
      <header>Registration form</header>
      <main>
        <form @submit.prevent="onSubmit">
          <div class="doubleRow">
            <fieldset>
              <label for="firstName">First name</label>
              <input id="firstName" v-model="data.firstName" type="text">
              <div v-for="error of v$.data.firstName.$errors" :key="error.$uid" class="input-errors">
                <div class="error-msg">
                  {{ error.$message }}
                </div>
              </div>
            </fieldset>

            <fieldset>
              <label for="lastName">Last name</label>
              <input id="lastName" v-model="data.lastName" type="text" @blur="v$.data.lastName.$touch">
              <div v-for="error of v$.data.lastName.$errors" :key="error.$uid" class="input-errors">
                <div class="error-msg">
                  {{ error.$message }}
                </div>
              </div>
            </fieldset>
          </div>
          <fieldset>
            <label for="email">Email</label>
            <input id="email" v-model="v$.data.email.$model" type="email">
            <div v-for="error of v$.data.email.$errors" :key="error.$uid" class="input-errors">
              <div class="error-msg">
                {{ error.$message }}
              </div>
            </div>
          </fieldset>
          <div class="doubleRow">
            <div>
              <fieldset>
                <label for="age">Age</label>
                <input id="age" v-model="v$.data.age.$model" type="number">
                <div v-for="error of v$.data.age.$errors" :key="error.$uid" class="input-errors">
                  <div class="error-msg">
                    {{ error.$message }}
                  </div>
                </div>
              </fieldset>
              <fieldset>
                <p>Select your gender</p>
                <label>
                  <input v-model="data.gender" type="radio" value="male">Male
                </label>
                <label>
                  <input v-model="data.gender" type="radio" value="female">Female
                </label>
                <label>
                  <input v-model="data.gender" type="radio" value="other">Other
                </label>
              </fieldset>
              <fieldset>
                <label for="country">
                  Country
                  <select id="country" v-model="data.country">

                    <option value="">
                      Please select country
                    </option>
                    <option v-for="country in countryOptions" :key="`country-${country.id}`" :value="country.id">
                      {{ country.name }}
                    </option>
                  </select>
                </label>
              </fieldset>
            </div>
            <fieldset>
              <p>Select your skill set</p>
              <label v-for="skill in skilsOptions" :key="`skill-${skill.id}`">
                <input v-model="data.skillSet" type="checkbox" :value="skill.id">
                <span>{{ skill.name }}</span>
              </label>
            </fieldset>
          </div>
          <button type="submit" class="primary">
            Submit✉️
          </button>
        </form>
      </main>
    </article>

    <article>
      <div v-if="isSubmited">
        <h2>Data viewer</h2>
        <ul>
          <li v-for="(value, key) in data" :key="key">
            {{ key }} is: {{ value }}
          </li>
        </ul>
      </div>
    </article>
  </section>
</template>

<style scoped>
.pageSection {
  max-width: 1000px;
  margin: 4rem auto 0;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}
.doubleRow{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
}
</style>

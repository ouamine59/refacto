<template>
  <form @submit.prevent="handleSubmit">
    <!-- <BaseInput
      label="Username"
      v-model="form.username"
      placeholder="Enter your username"
      :errorMessage="usernameError"
      :showError="!$v.form.username.$pending && $v.form.username.$error"
      @blur="$v.form.username.$touch()"
    />

    <BaseInput
      label="Email"
      type="email"
      v-model="form.email"
      placeholder="Enter your email"
      :errorMessage="emailError"
      :showError="!$v.form.email.$pending && $v.form.email.$error"
      @blur="$v.form.email.$touch()"
    />

    <BaseInput
      label="Password"
      type="password"
      v-model="form.password"
      placeholder="Enter your password"
      :errorMessage="passwordError"
      :showError="!$v.form.password.$pending && $v.form.password.$error"
      @blur="$v.form.password.$touch()"
    /> -->

    <button type="submit">Submit</button>
  </form>
</template>

<script setup >
import { reactive, computed } from 'vue';
//import useVuelidate from '@vuelidate/core';
//import { required, minLength, email } from '@vuelidate/validators';
//import BaseInput from "./../components/BaseInput.vue";

const form = reactive({
  username: '',
  email: '',
  password: '',
});

const rules = {
  form: {
    username: { required, minLength: minLength(3) },
    email: { required, email },
    password: { required, minLength: minLength(6) },
  },
};

const v$ = useVuelidate(rules, { form });

const handleSubmit = () => { 
  v$.value.$touch();
  if (!v$.value.$invalid) {
    alert('Form submitted successfully!');
  }
};

const usernameError = computed(() =>
  !v$.value.form.username.required ? 'Username is required' :
  !v$.value.form.username.minLength ? 'Must be at least 3 characters' : ''
);

const emailError = computed(() =>
  !v$.value.form.email.required ? 'Email is required' :
  !v$.value.form.email.email ? 'Must be a valid email' : ''
);

const passwordError = computed(() =>
  !v$.value.form.password.required ? 'Password is required' :
  !v$.value.form.password.minLength ? 'Must be at least 6 characters' : ''
);
</script>

<style>
button {
  margin-top: 1rem;
  padding: 0.5rem 1rem;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>


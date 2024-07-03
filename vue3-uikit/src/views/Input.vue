<script setup>
import { ref, computed } from "vue";
import useVuelidate from "@vuelidate/core";
import {
  helpers,
  minLength,
  email,
  maxLength,
  numeric,
  sameAs,
} from "@vuelidate/validators";
import Input from "@/components/Input.vue";
import Button from "@/components/Button.vue";

const nameField = ref("");
const emailField = ref("");
const luckyField = ref("");
const passwordField = ref("");
const confirmPasswordField = ref("");
const frontField = ref('')

const musBeFront = (value) => value.includes('front')

const rules = computed(() => ({
  nameField: {
    minLength: helpers.withMessage(
      "Минимальная длина: 3 символа",
      minLength(3)
    ),
  },
  emailField: {
    email: helpers.withMessage("Вы ввели неверный email", email),
  },
  luckyField: {
    maxLength: helpers.withMessage(
      "Максимальная длина: 2 символа",
      maxLength(2)
    ),
    numeric: helpers.withMessage("Вы можете ввести только цифры", numeric),
  },
  confirmPasswordField: {
    sameAsPassword: helpers.withMessage(
      "Пароли не совпадают",
      sameAs(passwordField.value)
    ),
  },
  frontField: {
   frontField: helpers.withMessage('Строка должна содержать слово Front', musBeFront)
  }
}));

const v = useVuelidate(rules, {
  nameField,
  emailField,
  luckyField,
  passwordField,
  confirmPasswordField,
  frontField
});

const submitForm = () => {
   v.value.$touch()
   console.log(v.value.$error)
   if (v.value.$error) return
   alert('Form submited')
}
</script>
<template>
    <h1 class="heading-1">Input</h1>
    <form @submit.prevent="submitForm">
    <Input
      label="Your name"
      name="name"
      placeholder="Input your name"
      v-model:value="v.nameField.$model"
      :error="v.nameField.$errors"
    />
    <Input
      label="Your email"
      name="email"
      placeholder="Input your email"
      v-model:value="v.emailField.$model"
      :error="v.emailField.$errors"
    />
    <Input
      label="Lucky number"
      name="number"
      type="number"
      placeholder="Input your lucky number"
      v-model:value="v.luckyField.$model"
      :error="v.luckyField.$errors"
    />
    <Input
      label="Password"
      name="password"
      type="password"
      placeholder="Input password"
      v-model:value="passwordField"
    />
    <Input
      label="Confirm password"
      name="confirmPassword"
      type="password"
      placeholder="Confirm your password"
      v-model:value="v.confirmPasswordField.$model"
      :error="v.confirmPasswordField.$errors"
    />
    <Input
      label="Front string"
      name="front"
      placeholder="Input string with front"
      v-model:value="v.frontField.$model"
      :error="v.frontField.$errors"
    />

    <Button label="Submit" color="primary" />
  </form>
</template>

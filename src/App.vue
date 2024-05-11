<template>
  <Form @submit="handleSubmit">
    <DynamicForm :schema="formSchema" />
    <button type="submit">Submit</button>
  </Form>
</template>

<script setup lang="ts">
import DynamicForm from './components/DynamicForm.vue';
import { Form } from 'vee-validate';
import * as Yup from 'yup';
import axios from 'axios';

const formSchema = {
  fields: [
    {
      label: 'Your Name',
      name: 'name',
      as: 'input',
      rules: Yup.string().required(),
    },
    {
      label: 'Your Email',
      name: 'email',
      as: 'input',
      rules: Yup.string().email().required(),
    },
    {
      label: 'Your Password',
      name: 'password',
      as: 'input',
      type: 'password',
      rules: Yup.string().min(6).required(),
    },
    {
      label: 'Select an Option',
      name: 'selectOption',
      as: 'v-select',
      rules: Yup.mixed().required(),
      options: [
        { label: 'Option 1', value: 'option1' },
        { label: 'Option 2', value: 'option2' },
        { label: 'Option 3', value: 'option3' },
      ],
    },
  ],
};

const handleSubmit = async (values) => {
  console.log(values)
};
</script>
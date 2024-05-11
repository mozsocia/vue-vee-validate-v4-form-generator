<template>
  <DynamicForm :schema="formSchema" />
</template>

<script setup lang="ts">
import DynamicForm from './components/DynamicForm.vue';
import * as Yup from 'yup';

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
  ],
};
</script>

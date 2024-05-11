<template>
  <div v-for="{ as, name, label, children, ...attrs } in schema.fields" :key="name">
    <label :for="name">{{ label }}</label>
    <Field
      :as="as === 'v-select' ? vSelect : as"
      :id="name"
      :name="name"
      v-bind="attrs"
    >
      <template v-if="children && children.length">
        <component
          v-for="({ tag, text, ...childAttrs }, idx) in children"
          :key="idx"
          :is="tag"
          v-bind="childAttrs"
        >
          {{ text }}
        </component>
      </template>
    </Field>
    <ErrorMessage :name="name" />
  </div>
</template>

<script setup>
import { Field, ErrorMessage } from 'vee-validate';
import vSelect from 'vue-select';

defineProps({
  schema: {
    type: Object,
    required: true,
  },
});
</script>
<template>
  <form>
    <div>
      <input v-model="usernameValue" type="text" placeholder="Prénom" />
    </div>
    <p v-if="errorMessage">{{ errorMessage }}</p>
  </form>
</template>

<script setup lang="ts">
import { useField } from 'vee-validate';
import { z } from 'zod';
import { toFieldValidator } from '@vee-validate/zod';

const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(false);
  }, 3000);
});

const {
  value: usernameValue,
  errorMessage,
  meta,
  handleBlur,
  handleChange,
} = useField(
  'password',
  toFieldValidator(z.string.min(5, { message: 'Trop court !' }))
);
</script>

<style scoped lang="scss">
.success {
  border-color: green;
}

.error {
  border-color: red;
}
</style>

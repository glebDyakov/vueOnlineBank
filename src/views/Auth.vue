<template>
  <form class="card" @submit.prevent="onSubmit">
    <h1>Войти в систему</h1>
    <div :class="['form-control', {invalid: eError}]">
      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" @blur="eBlur">
      <small v-if="eError">{{ eError }}</small>
  </div>
  <div :class="['form-control', {invalid: pError}]">
      <label for="password">Пароль</label>
      <input type="password" id="password" v-model="password" @blur="pBlur">
      <small v-if="pError">{{ pError }}</small>
    </div>
    <button :disabled="isSubmitting || isTooManyAttempts" class="btn primary" type="submit">Войти</button>
    <div class="text-danger" v-if="isTooManyAttempts">Вы слишком часто пытаетесь войти в систему. Попробуйте позже</div>
  </form>
</template>

<script>
import {computed, watch} from 'vue'
import { useField, useForm } from 'vee-validate'
import * as yup from 'yup'
import {useLoginForm} from '../use/login-form'

export default {
  setup(){
    return {...useLoginForm()}
  },
}
</script>

<template>
  <div>
    <input type="number" placeholder="Введите возраст" v-model.number="age" /> <br />
    <input type="text" placeholder="Введите пароль" v-model="password" />
    <p v-if="isValidPassword == false">Пароль не соответствует требованиям</p>
    <p v-if="isValidAge == false">Возраст не соответствует требованиям</p>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const password = ref<any>('test')
const age = ref<number>(0)
const regex = /^(?=.*\d)(?=.*[A-Z])(?=.*[\W\S]).*$/

const isValidAge = computed(() => {
  console.log('isValidAge called')
  if (age.value < 15) return false
  return true
})

const isValidPassword = computed(() => {
  console.log('isValidPassword called')
  if (password.value.length < 7) return false
  else if (regex.test(password.value)) return false
  return true
})
</script>

<style scoped></style>

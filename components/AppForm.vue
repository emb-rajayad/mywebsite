<script setup lang="ts">
import type { FormError, FormErrorEvent, FormSubmitEvent } from '#ui/types'

const state = reactive({
  name: undefined,
  email: undefined,
  mobile: undefined,
  comment: undefined
})

const validate = (state: any): FormError[] => {
  const errors = []
  if (!state.name) errors.push({ path: 'name', message: 'Required' })
  if (!state.email) errors.push({ path: 'email', message: 'Required' })
  if (!state.mobile) errors.push({ path: 'mobile', message: 'Required' })
  if (!state.comment) errors.push({ path: 'comment', message: 'Required' })
  return errors
}

async function onSubmit (event: FormSubmitEvent<any>) {
  // Do something with data
  console.log(event.data)
}

async function onError (event: FormErrorEvent) {
  const element = document.getElementById(event.errors[0].id)
  element?.focus()
  element?.scrollIntoView({ behavior: 'smooth', block: 'center' })
}
</script>
<template>
  <div class="flex flex-col  items-center">
    <UForm :validate="validate" :state="state" class="space-y-4 text-white" @submit="onSubmit" @error="onError">
    <UFormGroup label="Name" name="name">
      <UInput v-model="state.name" />
      </UFormGroup>
      <UFormGroup label="Email" name="email">
      <UInput v-model="state.email"  placeholder="you@example.com" icon="i-heroicons-envelope" />
      </UFormGroup>

      <UFormGroup label="Mobile" name="mobile">
      <UInput v-model="state.mobile" />
      </UFormGroup>
      <UFormGroup name="comment" label="Comment">
      <UTextarea v-model="state.comment" />
    </UFormGroup>
      <UButton type="submit">
      Submit
      </UButton>
  </UForm>
  </div>
  </template>
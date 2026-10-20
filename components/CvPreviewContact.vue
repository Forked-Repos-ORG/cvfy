<script lang="ts" setup>
import { useCvState } from '~/data/useCvState'

const { formSettings } = useCvState()

const emailHref = computed(() => {
  return `mailto:${formSettings.value.email}`
})
const phoneNumberHref = computed(() => {
  return `tel:${formSettings.value.phoneNumber.replace(/[^\d+]/g, '')}`
})
const location = computed(() => formSettings.value.location?.trim())
</script>

<template>
  <section
    class="cv__section"
    :class="formSettings.layout === 'one-column' && 'mt-0'"
  >
    <h4
      v-if="formSettings.layout !== 'one-column'"
      class="cv__section-title"
    >
      {{ $t("contact") }}
    </h4>
    <div
      class="flex"
      :class="formSettings.layout === 'one-column' ? 'flex-wrap gap-2' : 'flex-col'"
    >
      <div
        v-if="formSettings.email"
        class="cv__icon-wrapper"
      >
        <svg class="cv__icon">
          <use href="@/assets/sprite.svg#email" />
        </svg>
        <a
          :href="emailHref"
          rel="noopener"
        >{{ formSettings.email }}</a>
      </div>
      <div
        v-if="formSettings.phoneNumber"
        class="cv__icon-wrapper"
      >
        <svg class="cv__icon">
          <use href="@/assets/sprite.svg#phone" />
        </svg>
        <a
          :href="phoneNumberHref"
          rel="noopener"
        >{{ formSettings.phoneNumber }}</a>
      </div>
      <div
        v-if="location || formSettings.address || formSettings.city || formSettings.country"
        class="cv__icon-wrapper"
      >
        <svg class="cv__icon">
          <use href="@/assets/sprite.svg#location" />
        </svg>
        <span
          v-if="location"
          class="address"
        >{{ location }}</span>
        <span
          v-else
          class="address"
        >
          <template v-if="formSettings.address">{{ formSettings.address }}, </template>
          <template v-if="formSettings.city">{{ formSettings.city }}, </template>
          <template v-if="formSettings.country">{{ formSettings.country }}</template>
        </span>
      </div>
    </div>
  </section>
</template>

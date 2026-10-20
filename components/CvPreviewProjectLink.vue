<script lang="ts" setup>
interface Props {
  title: string
  href: string
}

defineProps<Props>()
</script>

<template>
  <!-- rel="noopener" -->
  <a
    v-if="href"
    class="w-fit flex items-center font-medium italic text-underline"
    target="_blank"
    :href="`https://${href.replace(/https?:\/\//, '')}`"
    :aria-label="`Open ${title} project in new tab`"
  >
    {{ href.replace(/https?:\/\//, "") }}
    <svg class="ml-1 size-4">
      <use href="@/assets/sprite.svg#open-in-new-tab" />
    </svg>
  </a>
</template>

<style lang="postcss" scoped>
/* a border, not an absolutely positioned ::before, so the link stays in normal paint order (PDF text order) */
.text-underline {
    border-bottom: 1px solid #334155; /* slate-700 */
}
</style>

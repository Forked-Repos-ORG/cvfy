<script lang="ts" setup>
</script>

<template>
  <div class="flex justify-between gap-1">
    <div class="flex flex-col gap-1">
      <div class="flex flex-col justify-center">
        <CvPreviewName />
        <CvPreviewTitle />
      </div>
      <div class="flex flex-col gap-1">
        <CvPreviewContact />
        <CvPreviewSocial />
      </div>
      <CvPreviewAbout class="mt-3" />
    </div>
    <CvProfileImageViewer class="rounded ml-2" />
  </div>

  <CvPreviewSkills />

  <CvPreviewExperience />

  <CvPreviewEducation />

  <CvPreviewProjects />
</template>

<style lang="postcss" scoped>
:deep(h4.cv__section-title) {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-shrink: 0;
  word-break: keep-all;
}

:deep(h4.cv__section-title::after) {
  content: '';
  width: 100%;
  height: 2px;
  margin-left: 10px;
  background-color: var(--primary);
  border-radius: 10px;
}
</style>

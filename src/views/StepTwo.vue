<script setup>
import PageContainer from '@/components/Layout/PageContainer.vue'
import Step2Practice from '@/workshop/Step2Practice.vue'
import Step2Solution from '@/workshop/Step2Solution.vue'
</script>

<template>
  <PageContainer>
    <template v-slot:practice>
      <Step2Practice />
    </template>
    <template v-slot:solution>
      <Step2Solution />
    </template>
  </PageContainer>
</template>

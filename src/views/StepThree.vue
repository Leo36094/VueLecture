<script setup>
import PageContainer from '@/components/Layout/PageContainer.vue'
import Step3Practice from '@/workshop/Step3Practice.vue'
import Step3Solution from '@/workshop/Step3Solution.vue'
</script>

<template>
  <PageContainer>
    <template v-slot:practice>
      <Step3Practice />
    </template>
    <template v-slot:solution>
      <Step3Solution />
    </template>
  </PageContainer>
</template>

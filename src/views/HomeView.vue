<script setup>
import PageContainer from '@/components/Layout/PageContainer.vue'
import Step1Practice from '@/workshop/Step1Practice.vue'
import Step1Solution from '@/workshop/Step1Solution.vue'
</script>

<template>
  <div class="flex h-[calc(100vh-3rem)] flex-col items-center">
    <PageContainer>
      <template v-slot:practice>
        <Step1Practice />
      </template>
      <template v-slot:solution>
        <Step1Solution />
      </template>
    </PageContainer>
  </div>
</template>

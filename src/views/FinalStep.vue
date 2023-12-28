<script setup>
import PageContainer from '@/components/Layout/PageContainer.vue'
import FinalPractice from '@/workshop/FinalPractice.vue';
import FinalSolution from '@/workshop/FinalSolution.vue';
</script>

<template>
  <PageContainer>
    <template v-slot:practice>
      <FinalPractice />
    </template>
    <template v-slot:solution>
      <FinalSolution />
    </template>
  </PageContainer>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import BaseTitle from '@/components/BaseTitle.vue';
import useAPI from '@/composables/useAPI'
import MainScore from '@/components/MainScore.vue';

const { categories, getCategories } = useAPI()

onMounted(async () => {
  await getCategories()
} 
)


</script>

<template>
  <BaseTitle>TRIVIA APPLICTION - <MainScore></MainScore></BaseTitle> 
  <div class="grid flex-grow grid-cols-4 gap-12 m-20">
      <RouterLink v-for="category in categories" 
      :key="category.id"
      :to="`/question/category/${category.id}`"
      class="bg-teal-800 text-center flex h-32 items-center justify-center rounded-lg text-white border-4 border-teal-900 py-4 font-bold uppercase hover:cursor-pointer hover:text-yellow-600 hover:bg-yellow-100 hover:border-yellow-500 transition-colors duration-300"
      >
          {{ category.name }}
      </RouterLink>
  </div>
  
</template>

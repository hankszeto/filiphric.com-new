<template>
  <NuxtLayout>
    <div v-for="course in data" :key="course.uuid">
      <NuxtLink :to="'/courses/' + course.slug" class="text-4xl font-semibold">
        {{ course.title }}
      </NuxtLink>
      <div>{{ course.description }}</div>
    </div>
  </NuxtLayout>
</template>
<script setup lang="ts">
const supabase = useSupabaseClient()

const { data } = await supabase
  .from('courses')
  .select('title, slug, description, uuid')

</script>

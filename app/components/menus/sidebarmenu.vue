<template>
  <div>
    <h5 class="menuh5">{{ sidebar?.name }}</h5>
    <v-list v-for="item in sidebar?.menus" :key="item">
      <v-list-item :title="item?.name" :value="item?.name" :prepend-icon="item?.icon" :href="item?.url"></v-list-item>
    </v-list>
  </div>
</template>

<script setup>
const { $directus, $readItem } = useNuxtApp()
const route = useRoute()

const { data: sidebar } = await useAsyncData('sidebar', () => {
  return $directus.request($readItem('navigation', '66'))
})
</script>
<template>
    <div>
        <v-app-bar-title>
            <NuxtLink class="logobrand" href="/">
                <v-icon start size="small" icon="fa:fas fa-calculator"></v-icon>
                <p class="logotext">{{ blocksSiteoverview?.name }}</p>
            </NuxtLink>
        </v-app-bar-title>
    </div>
</template>

<script setup>
    import {
        ref
    } from 'vue'

    const {
        $directus,
        $readItem
    } = useNuxtApp()

    const {
        data: blocksSiteoverview
    } = await useAsyncData('blocksSiteoverview', () => {
        return $directus.request($readItem('page_blocks', '13', {
            fields: ['*', 'media.*.*'],
        }))
    })
</script>
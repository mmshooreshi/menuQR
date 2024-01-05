<template>
    <div>
        <ul>
            <li v-for="slug in slugs" :key="slug">
                <nuxt-link :to="`/menus/${slug}`">{{ slug }}</nuxt-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    async asyncData({ $http }) {
        // Fetch the list of PDF slugs from the static JSON file
        try {
            const slugs = await $http.$get('/pdfList.json');
            return { slugs };
        } catch (e) {
            // Handle error (e.g., file not found)
            return { slugs: [] };
        }
    }
}
</script>

<style scoped>
/* Component styles */
</style>
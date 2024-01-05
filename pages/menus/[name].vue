<template>
    <div class="pdf-container">

        <iframe v-if="pdfExists" style="" :src="pdf" frameborder="0" height="500px" width="100%"></iframe>

        <div v-else>
            PDF not found
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const pdf = ref(null);
const pdfExists = ref(false);

onMounted(() => {
    if (process.client) {
        const pdfFileName = `${route.params.name}.pdf`;
        const pdfPath = `/menus/${pdfFileName}`; // Ensure this path is correct for your application
        // Here we directly set the value of pdf to the path.
        // In practice, you might want to check for the existence of the PDF file before assigning it.
        pdf.value = pdfPath + "#toolbar=0";
        pdfExists.value = true;
    }
});




</script>

<style >
body,
html {
    margin: 0;
    padding: 0;
    height: 100%;
    overflow: hidden;
    /* Optional: Remove scrolling on body */
}

.pdf-container {
    height: 100vh;
    /* Full viewport height */
    width: 100vw;
    /* Full viewport width */
}

.pdf-container iframe {
    margin-top: -5vh;
    margin-bottom: -5vh;
    width: 100%;
    height: 110vh;
    border: none;
    /* Removes the frame border */
    display: block;
}
</style>
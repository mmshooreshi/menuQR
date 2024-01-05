<template>
    <div class="pdf-container">
        <object v-if="pdfExists" type="application/pdf" :data="pdf" style="margin-top: -40px;" width="100%" height="110%">
            <p>PDF not found</p>
        </object>
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
    const pdfFileName = `${route.params.name}.pdf`;
    const pdfPath = `/menus/${pdfFileName}`; // Ensure this path is correct for your application
    pdf.value = pdfPath;

    // You would typically execute a check here to ensure the PDF exists.
    // If that check passes, set 'pdfExists' to true. 
    // For this example, we'll set it to true by default.
    pdfExists.value = true;
});
</script>
<!-- 
<style>
.pdf-container {
    width: 100%;
    height: 500px;
    overflow: hidden;
    /* Optional: hide the overflow if it's larger than you want */
}

.pdf-container object {
    display: block;
    width: 100%;
    height: 100%;
}
</style> -->

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
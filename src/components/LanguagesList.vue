<script>

import LanguageCard from './LanguageCard.vue';

export default {

    name: "LanguagesList",
    components: { LanguageCard },
    data() {
        return {
            languages: [
                "html",
                "css",
                "bootstrap",
                "javascript",
                "vue",
                "vite",
                "php",
                "laravel"
            ]
        }
    }

}

</script>


<template>

    <div class="row">

        <LanguageCard v-for="(language, index) in languages" :language="language" />

    </div>



</template>


<style lang="scss" scoped>

</style>
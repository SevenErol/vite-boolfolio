<script>

import AppHeader from '../components/AppHeader.vue';
import AppBanner from '../components/AppBanner.vue';

import LanguagesList from '../components/LanguagesList.vue';

export default {
    name: 'AppAbout',
    components: { AppHeader, AppBanner, LanguagesList },
    data() {
        return {
            message: " About me "
        }
    }
}
</script>

<template>

    <AppHeader />

    <AppBanner :message="message" />

    <section id="card_section">

        <div class="container p-5">
            <h1 class="animate__animated animate__fadeInDown">About Page</h1>
            <p class="animate__animated animate__fadeInDown">
                Hey, you are still here that's great! In this section you can have an overview of all the languages i
                learned during my journey in Boolean.
            </p>

            <LanguagesList class="animate__animated animate__fadeInDown" />


        </div>

    </section>


</template>


<style lang="scss" scoped>
#card_section {
    background-color: #f1f1f1;
}
</style>
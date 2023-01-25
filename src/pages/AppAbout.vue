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

    <div class="container p-5">
        <h1>About Page</h1>
        <p class="lead">
            Hey, you are still here that's great! In this section you can have an overview of all the languages i
            learned during my journey in Boolean.
        </p>

        <LanguagesList />


    </div>
</template>


<style lang="scss" scoped>

</style>
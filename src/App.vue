<script>
import AppHeader from "./components/AppHeader.vue";

import ProjectCard from "./pages/ProjectCard.vue";

export default {
    components: {
        AppHeader,
        ProjectCard
    }
}
</script>

<template>

    <AppHeader />

    <router-view></router-view>

    <!-- <ProjectCard /> -->

</template>

<style lang="scss">
@use './styles/general.scss';
</style>

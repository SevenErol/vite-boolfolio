<script>
import HelloWorld from './components/HelloWorld.vue';

import ProjectCard from "./components/ProjectCard.vue";

export default {
    components: {
        HelloWorld,
        ProjectCard
    }
}
</script>

<template>

    <ProjectCard />

</template>

<style lang="scss">
@use './styles/general.scss';
</style>

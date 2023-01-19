<script>
import HelloWorld from './components/HelloWorld.vue';

import axios from 'axios';

export default {
    components: {
        HelloWorld,
    },
    data() {
        return {
            projects: null,
            base_api_url: 'http://127.0.0.1:8000',
            loading: true,
            error: null,
            maxLength: 100
        }
    },

    methods: {
        getPosts(url) {
            axios
                .get(url)
                .then(response => {
                    console.log(response.data.results.data);
                    this.projects = response.data.results.data;
                    this.loading = false
                })
                .catch(error => {
                    console.error(error)
                    this.error = error.message
                    this.loading = false
                })
        },
        getImagePath(path) {
            console.log(path);
            if (path) {
                return this.base_api_url + '/storage/' + path
            }
            return '/img/no-image.png'
        },
        /**
         * 
         * @param {string} text the post body
         */
        trimDescription(text) {
            if (text !== null && text.length > this.maxLength) {
                return text.slice(0, this.maxLength) + '...'
            }
            return text
        },
        prevPage(url) {
            console.log(url)
            this.getPosts(url)
        },
        nextPage(url) {
            console.log(url)
            this.getPosts(url)
        }
    },
    mounted() {
        this.getPosts(this.base_api_url + '/api/projects');
    }

}
</script>

<template>
    <div class="container p-5">
        <div class="row">
            <div class="col-3 d-flex gy-4" v-for="project in projects">
                <div class="card">
                    <img :src="getImagePath(project.cover_image)" class="card-img-top img-fluid" alt="#">
                    <div class="card-body">
                        <h5 class="card-title">{{ project.title }}</h5>
                        <p class="card-text" v-if="project.description">{{ trimDescription(project.description) }}</p>
                        <p class="card-text" v-else>This project has no description yet, i am sorry.</p>
                        <div>
                            <strong>Types:</strong>
                            <ul>
                                <li v-if="project.type">{{ project.type.name }}</li>
                                <li v-else>No type for this project</li>
                            </ul>
                        </div>

                        <div>
                            <strong>Technologies:</strong>

                            <ul v-if="project.technologies.length > 0">
                                <li v-for="technology in project.technologies">{{ technology.name }}</li>
                            </ul>

                            <p v-else>Sorry there are no technologies in this project</p>
                        </div>

                        <a href="#" class="btn btn-primary">Go somewhere</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
@use './styles/general.scss';
</style>

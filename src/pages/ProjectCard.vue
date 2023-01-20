<script>
import axios from 'axios';

import AppHeader from '../components/AppHeader.vue';

export default {
    name: "ProjectCard",
    data() {
        return {
            projects: [],
            base_api_url: 'http://127.0.0.1:8000',
            loading: true,
            error: null,
            maxLength: 100,
            results: null
        }
    },

    components: { AppHeader },

    methods: {
        getPosts(url) {
            axios
                .get(url)
                .then(response => {
                    console.log(response.data.results);
                    this.projects = response.data.results.data;
                    this.results = response.data.results
                    this.loading = false
                })
                .catch(error => {
                    console.error(error)
                    this.error = error.message
                    this.loading = false
                })
        },
        getImagePath(path) {
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
            this.getPosts(url)
        },
        nextPage(url) {
            this.getPosts(url)
        }
    },
    mounted() {
        this.getPosts(this.base_api_url + '/api/projects');
    }
}

</script>


<template>

    <div class="container-fluid" v-if="results">

        <AppHeader />

        <div class="container p-5">
            <div class="row">
                <div class="col-3 d-flex gy-4" v-for="project in projects">
                    <div class="card">
                        <img :src="getImagePath(project.cover_image)" class="card-img-top img-fluid" alt="#">
                        <div class="card-body">
                            <h5 class="card-title">{{ project.title }}</h5>
                            <p class="card-text" v-if="project.description">{{ trimDescription(project.description) }}
                            </p>
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

                            <router-link class="btn btn-primary"
                                :to="{ name: 'single-project', params: { id: project.id } }" aria-current="page">Read
                                more<span class="visually-hidden">(current)</span></router-link>
                        </div>
                    </div>
                </div>
            </div>

            <nav aria-label="Page navigation" class="d-flex justify-content-center pt-5">
                <ul class="pagination    ">
                    <li class="page-item" v-if="results.prev_page_url" @click="prevPage(results.prev_page_url)">
                        <a class="page-link" aria-label="Previous">
                            <span aria-hidden="true">&laquo;</span>
                        </a>
                    </li>
                    <li class="page-item active" aria-current="page"><a class="page-link" href="#">{{
                        results.current_page
                    }}</a></li>

                    <li class="page-item" v-if="results.next_page_url" @click="nextPage(results.next_page_url)">
                        <a class="page-link" aria-label="Next">
                            <span aria-hidden="true">&raquo;</span>
                        </a>
                    </li>
                </ul>
            </nav>

        </div>

    </div>


    <div v-else class="d-flex justify-content-center align-items-center vh-100">
        <h2>Loading page ...</h2>
    </div>



</template>
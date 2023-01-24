<script>
import axios from 'axios'

import AppHeader from '../components/AppHeader.vue'

export default {
    name: 'SingleProject',
    components: { AppHeader },
    data() {
        return {
            project: null,
            loading: true,
            base_api_url: 'http://127.0.0.1:8000',
            message: null
        }
    },
    methods: {
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
        }
    },
    mounted() {
        const url = this.base_api_url + '/api/projects/' + this.$route.params.id
        console.log(url);
        axios.get(url)
            .then(response => {
                if (response.data.success) {
                    this.project = response.data.results
                    this.loading = false
                } else {
                    this.message = "404 not found"
                }
                console.log(response);
            }).catch(error => {
                console.log(error)
            })
    }
}
</script>

<template>

    <AppHeader />

    <div class="container-fluid" v-if="project">


        <div class="container py-5">
            <div class="row">
                <div class="col-10">
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
                </div>
                <div class="col-2">
                    <img :src="getImagePath(project.cover_image)" class="card-img-top img-fluid" :alt="project.title">
                </div>
            </div>
        </div>

    </div>



    <div v-else-if="message" class="d-flex justify-content-center align-items-center vh-100 bg-dark">
        <h2 class="text-white">{{ message }}</h2>
    </div>

    <div v-else class="d-flex justify-content-center align-items-center vh-100">
        <h2>Loading page...</h2>
    </div>


</template>




<style lang="scss" scoped>

</style>

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
            error: null
        }
    },

    methods: {
        getPosts(url) {
            axios
                .get(url)
                .then(response => {
                    console.log(response.data.results);
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
            return '/img/placeholder_600.png'
        },
        /**
         * 
         * @param {string} text the post body
         */
        trimBody(text) {
            if (text.length > this.max) {
                return text.slice(0, this.max) + '...'
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
    <div class="container">
        <div class="row row-cols-5">
            <div class="col" v-for="project in projects">
                <div class="card">
                    <h3>{{ project.title }}</h3>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
@use './styles/general.scss';

.vue-home {
    color: #2c3e50;
    background: #181818;
    transition: color 0.5s, background-color 0.5s;
    line-height: 1.6;
    font-family: Inter, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
        Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
    font-size: 15px;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
}

.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

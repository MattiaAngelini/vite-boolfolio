<script>
import axios from 'axios';
import SingleProject from './SingleProject.vue';

export default {
    name: 'ProjectList',
    components: {
        SingleProject
    },

    data() {
        return {
            currentPage: 1,
            prevPageUrl: null,
            nextPageUrl: null,
            projects: []
        };
    },
    methods: {
        getProjects(pageNumber) {
            
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                    page: pageNumber
                }
            })

            .then((response) => {
                this.projects = response.data.results.data;
                this.currentPage = response.data.results.current_page;
                this.prevPageUrl = response.data.results.prev_page_url;
                this.nextPageUrl = response.data.results.next_page_url;
            });
        }
    },
    mounted() {
        this.getProjects(this.currentPage);
    }
}
</script>

<template>

    <h1 class="text-center">Elenco dei Progetti:</h1>
    
    <!--Projects Cards-->
    <div class="d-flex justify-content-center flex-wrap gap-2">
        <SingleProject v-for="project in projects" :project="project"> </SingleProject>
    </div>

    <!-- Buttons Pagination ->(3) -->
    <ul class="pagination d-flex m-2 gap-3 justify-content-center">
        <div class="d-flex align-items-center">Page: {{ currentPage }}</div>
        <li v-if="prevPageUrl" class="page-item"><a class="page-link" @click="getProjects(currentPage - 1)">Previous</a></li>
        <li v-if="nextPageUrl" class="page-item"><a class="page-link" @click="getProjects(currentPage + 1)">Next</a></li>
    </ul>

</template>

<style scoped lang="scss">
</style>

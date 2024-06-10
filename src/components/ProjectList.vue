<script>
import axios from 'axios';

export default {
    name: 'ProjectList',

    data() {
        return {
            projects: []
        };
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects')
            .then((response) => {
                this.projects = response.data.results;
            });
        }
    },
    mounted() {
        this.getProjects();
    }
}
</script>

<template>
    <h1 class="text-center">Elenco dei Progetti:</h1>

    <section class="d-flex flex-wrap gap-2">

        <div v-for="project in projects">
            <div class="card" style="width: 18rem;">
                <img src="..." class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title">{{ project.name }}</h5>
                    <p v-if="project.summary" class="card-text">{{ project.summary }}</p>
                </div>
            </div>
        </div>

    </section>

</template>

<style scoped lang="scss">
</style>

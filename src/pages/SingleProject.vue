<script>

import axios  from 'axios';

export default {
  name: 'SingleProject',
  data() {
    return {
       project:null
    };
  },
  methods: {
    getProject() {
        axios.get(`http://127.0.0.1:8000/api/projects/${this.$route.params.slug}`)
        .then((response)=> {
            this.project = response.data.project;
        });
        
    }
  },
  mounted() {
        this.getProject();
  }
}
</script>

<template>

    <!--Single Project-->
    <section class="container">
        <h1>Single project:</h1> 
        <!--Name-->
        <div v-if="project">
          <h2>{{ project.name }}</h2>
        </div>
        <!--Summary-->
        <div v-if="project">
          <h2>{{ project.summary }}</h2>
        </div>
        <!--Cover Image-->
        <div v-if="project">
            <img :src="`http://127.0.0.1:8000/storage/${project.cover_image}`" >
        </div>
    </section>

</template>

<style scoped lang="scss">
</style>

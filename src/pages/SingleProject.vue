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
        
        <div v-if="project">
       
          <h1>Name project: </h1>     
          <p>{{ project.name }}</p>
       
          <h2>Summary project: </h2>  
          <p>{{ project.summary }}</p>
         
          <h3>Image:</h3>
            <img :src="`http://127.0.0.1:8000/storage/${project.cover_image}`" >
        </div>
        
    </section>

</template>

<style scoped lang="scss">
</style>

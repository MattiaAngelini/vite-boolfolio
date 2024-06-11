<script>


export default {
    name: 'SingleProjectDetails',
    props: {
        project: Object
    }

  
    }

</script>

<template>
    
    <!--Single Card 'project'-->
    <div class="">
        <div class="card" style="width: 18rem;">          
            <div class="card-body">
                <h5 class="card-title">{{ project.name }}</h5>
                <p v-if="project.summary" class="card-text">{{ project.summary }}</p>
                <router-link :to="{name: 'single-project', params: {slug: project.slug}}"><button class="btn btn-primary">Show Project</button></router-link>
            </div>
        </div>
    </div>
    
</template>

<style scoped lang="scss">
</style>

<script>


export default {
    name: 'SingleProject',
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
            </div>
        </div>
    </div>
    
</template>

<style scoped lang="scss">
</style>

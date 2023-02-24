<template lang="">
        <img  class="card-img-top"
                    :src="courses.image"
                    :alt="courses.titre">
            <div class="card-body">
                <h5 class="card-title">{{ courses.title }}</h5>
                <p class="card-text">
                This is a wider card with 
                supporting text below as a
                natural lead-in to additional content.
                This content is a little bit longer.</p>
                <button class="btn btn-sm btn-danger" @click="deleteOne(id)">DELETE</button>
                <button class="btn btn-sm btn-dark">{{ courses.category }}</button>
                <div class="my-3">
                    <span class="badge bg-primary ml-2" v-for="tags in courses.tags">{{ tags }}</span>
                </div>
            </div>
</template>
<script>
export default {
    props:['courses'],
    methods:{
        deleteOne(id){
            this.$emit('delete',id)
        }
        
    }

}
</script>
<style lang="">
    
</style>
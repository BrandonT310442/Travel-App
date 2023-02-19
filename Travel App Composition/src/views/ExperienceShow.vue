<template>
    <section>
        <h1>{{ experience.name }}</h1>
        <img :src="`/images/${experience.image}`" alt="">
        <p>{{ experience.description }}</p>
    </section>
</template>

<script>
import sourceData from '../data.json'
import { ref, computed } from 'vue';

export default{
    props: {
        id:{type:Number, required:true},
        experienceSlug:{type:String, required:true}
    },

    setup(props){
        const description = computed(()=>{
            return sourceData.destinations.find(destination => destination.id === props.id)
        })
        const experience = computed(()=>{
            return description.value.experiences.find(experience => experience.slug === props.experienceSlug)
        })
        return {
            description,
            experience
        }
    }
  
}
</script>
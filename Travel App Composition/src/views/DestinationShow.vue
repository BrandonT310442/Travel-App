<template>
    <div>
    <section v-if="destination" class="destination">
        <h1>{{ destination.name }}</h1>
        <GoBack />
        <div class="destination-details">
            <img :src="`/images/${destination.image}`" alt="">
            <p>{{ destination.description }}</p>
        </div>
    </section>
    <section class="experiences">
    <h2>Top Experiences In {{ destination.name }}</h2>
    <div class="cards">
        <router-link
        v-for="experience in destination.experiences"
    :key="experience.slug"
    :to="{name:'experience.show', params: {experienceSlug:experience.slug} }"
        >
            <ExperienceCard
    
    :experience="experience"
    />
        </router-link>
        
    </div>
    <router-view />
</section>
</div>
</template>

<script>
import sourceData from '../data.json'
import ExperienceCard from '../components/ExperienceCard.vue'
import GoBack from '../components/GoBack.vue'
import { ref, computed } from 'vue';

export default{
    components:{ ExperienceCard, GoBack},
 props: {
    id:{type:Number, required:true},
 },
 setup(props){
    const destination = computed(()=>{
        return sourceData.destinations.find(destination => destination.id === props.id)
    })
    return {
        destination
    }
 }


   
}

</script>
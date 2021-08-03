<template>
    <div>
        <section class="destination">
            <h1>{{destination.name}}</h1>
            <div class="destination-details">
                <img :src="require(`@/assets/${destination.image}`)" :alt="destination.name">
                <p>{{destination.description}}</p>
            </div>
        </section>

        <section class="experiences">
            <h2>Top experiences in {{destination.name}}</h2>
            <div class="cards">
                <div 
                    v-for="experience in destination.experiences"
                    :key="experience.slug"
                    class="card"
                >
                    <img 
                        :src="require(`@/assets/${experience.image}`)" 
                        :alt="experience.name"
                    />
                    <span class="experience_text">
                        {{experience.name}}
                    </span>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
import store from '@/store.js';
export default {
    data() {
        return {
            destinationId: this.$route.params.id
        }
    },
    computed: {
        destination: function() {
            return store.destinations.find(el => el.id === this.destinationId)
        }
    }
}
</script>

<style scoped>
img {
    max-width: 600px;
    width: 100%;
    height: auto;
    max-height: 400px;
}

.destination-details {
    display: flex;
    justify-content: space-between;
}

p {
    margin:0 40px;
    font-size: 18px;
    text-align: left;
}
</style>
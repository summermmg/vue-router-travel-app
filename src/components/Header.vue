<template>
    <nav>
        <ul class="nav-links">
            <li class="links" >
                <router-link to="/">Home</router-link>
            </li>
            <li
                v-for="destination in destinations"
                :key="destination.name"
                class="links"
            >
                <router-link 
                    :to="{name: 'DestinationDetails',params:{id: destination.id}}"
                >
                    {{destination.name}}
                </router-link>
            </li>
        </ul>
    </nav>
</template>

<script>
import store from '@/store.js'
export default {
    data() {
        return {
            destinationId: this.$route.params.id,
            destinations: store.destinations
        }
    }
}
</script>

<style scoped>
    nav {
    padding: 30px;
    display: flex;
    justify-content: center;
    }

    nav a {
    font-weight: bold;
    color: #2c3e50;
    margin: 0 20px;
    }

    nav a.router-link-exact-active {
    color: #42b983;
    }
    .nav-links {
        display: flex;
    }
    .links {
        list-style: none;
        padding-right: 20px;
    }
    .link:hover {
        text-decoration: underline;
    }

</style>

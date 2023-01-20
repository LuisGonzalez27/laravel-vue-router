<template>
    <section v-if="project">
        <h1>{{ project.name }}</h1>
        
        <img :src="`${store.imagePath}${project.cover_image}`" class="card-img-top" :alt="project.name">
        <p>{{ project.content }}</p>
        <div v-if="project.category">
            <h5>Category: {{ project.category.name }}</h5>
        </div>
        <div v-else="project.category">
            <h5>Nessuna category</h5>
        </div>

        <div v-if="project.technologies && project.technologies.length > 0">
            <h5>Tecnologies</h5>
            <div>
                Project singolo
                <span v-for="(technology, index) in project.technologies" :key="index" class="badge text-bg-info">{{ technology.name }}</span>
            </div>
        </div>
    </section>
    <section v-else>Loading</section>
</template>

<script>
import axios from 'axios';
import { store } from '../store';

export default {
    name: 'SingleProject',
    data() {
        return {
            store,
            project: null,
        }
    },
    methods: {
        getProject() {
            console.log(this.$route);
            axios.get(`${this.store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((response) => {
                console.log(response.data.results);
                if (response.data.success) {
                    //console.log(response.data.results);
                    this.project = response.data.results;
                } else {
                    //console.log(this.$router);
                    this.$router.push({ name: 'not-found' });
                }
            });
        }
    },
    mounted() {
        this.getProject();
    },

    

}
</script>

<style lang="scss" scoped>
.card-img-top {
    width: 300px;
}
</style>
<template>
    <div class="card" style="width: 18rem; height: 30rem">
        <div class="test-img">
            <img :src="`${store.imagePath}${project.cover_image}`" class="card-img-top" :alt="project.name">
            <!-- Sistemare default img -->
            <!-- <img v-if="project.cover_image" :src="`${store.imagePath}${project.cover_image}`" :alt="project.name"> -->
            <!-- <img v-else="project.cover_image" src="https://via.placeholder.com/150"> -->
        </div>
        <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ truncateContent }}</p>
            <router-link class="btn btn-primary" :to="{name: 'single-project', params:{ slug: project.slug }}">
                Vedi il project
            </router-link>
        </div>
    </div>
</template>

<script>
import { store } from '../store';
export default {
    name: 'ProjectCard',
    props: ['project'],
    data() {
        return {
            store,
            contentMaxLen: 100
        }
    },
    computed: {
        truncateContent() {
            if (this.project.content.length > this.contentMaxLen) {
                return this.project.content.substr(0, this.contentMaxLen) + '...';
            }
            return this.project.content;
        }
    }

}
</script>

<style lang="scss" scoped>

img {
  max-width: 100%;
}
.test-img{
    height: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>
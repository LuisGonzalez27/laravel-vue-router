<template>
    <section>
        <h1>Lista dei project</h1>
        <div class="row">
            <div class="col-12 col-md-3" v-for="(project, index) in projects" :key="project.id">
                <ProjectCard :project="project" />
            </div>
        </div>

        <nav aria-label="..." class="pt-3">
            <ul class="pagination">
                <li class="page-item" :class="{'disabled': currentPage === 1}">
                    <button class="page-link" :disabled="currentPage === 1" @click="getProjects(currentPage - 1)">Previous</button>
                </li>
                <li class="page-item" v-for="n in lastPage">
                    <button class="page-link" @click="getProjects(n)">{{n}}</button>
                </li>
                <li class="page-item" :class="{'disabled': currentPage === lastPage}">
                    <button class="page-link" :disabled="currentPage === lastPage" @click="getProjects(currentPage + 1)">Next</button>
                </li>
            </ul>
        </nav>

    </section>
</template>

<script>
import axios from "axios";
import { store } from "../store";
import ProjectCard from '../components/ProjectCard.vue';

    export default {
        name: 'ProjectList',
        components: {
            ProjectCard
        },
        data(){
            return{
                store,
                projects: [],
                currentPage: 1,
                lastPage: null,
                total: 0,
            }
        },
        methods:{
            getProjects(pagenum){
                axios.get(`${this.store.apiBaseUrl}/projects`,{params: { page: pagenum}}).then((response) => {
                    // console.log(response.data.results);
                    this.projects = response.data.results.data;
                    this.currentPage = response.data.results.current_page;
                    this.lastPage = response.data.results.last_page;
                    this.total = response.data.results.total;
                });
            },
        },
        mounted() {
            this.getProjects(1);
        },
    }
</script>

<style lang="scss" scoped>

</style>
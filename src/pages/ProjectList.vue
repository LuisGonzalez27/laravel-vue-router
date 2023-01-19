<template>
    <section>
        
    </section>
</template>

<script>
import axios from "axios";
import { store } from "../store";

    export default {
        name: 'ProjectList',
        data(){
            return{
                store,
                projects: []
            }
        },
        methods:{
            getProjects(){
                axios.get(`${this.store.apiBaseUrl}/projects`).then((response) => {
                    // console.log(response.data.results);
                    this.projects = response.data.results.data;
                });
            }
        },
        mounted() {
            this.getProjects();
        },
    }
</script>

<style lang="scss" scoped>

</style>
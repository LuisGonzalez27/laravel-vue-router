<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
            <div class="container-fluid">
                <a class="navbar-brand" href="#"></a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
                    aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent">
                    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                        <li class="nav-item" v-for="(link, index) in menuLinks" :key="index">
                            <router-link :to="{name : link.routeName}" active-class="my-active" class="nav-link">
                                {{ link.label }}
                            </router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </header>
</template>

<script>
    export default {
        name: 'AppHeader',
    data() {
        return {
            menuLinks: [
                {
                    label: "Home",
                    routeName: "home",
                },
                {
                    label: "Projects",
                    routeName: "projects",
                },
                {
                    label: "About",
                    routeName: "about",
                },
                {
                    label: "Contacts",
                    routeName: "contact",
                },
            ],
        };
    },
    }
</script>

<style lang="scss" scoped>

</style>
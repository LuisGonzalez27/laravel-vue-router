<template>
    <!-- Section Hero -->
    <section class="my-section hero align-items-stretch">
        <div class="hero-first d-flex flex-column justify-content-center align-items-center">
            <img class="hero-img-developer rounded-circle" src="./../assets/img/developer.svg" alt="img developer">
            <h1>Hi, my name is Luis Miguel Gonzalez Castellanos</h1>
            <h2>I'm a student of Boolean Careers class #74</h2>
        </div>
        <div>
            <img class="hero-down-img img-fluid" src="./../assets/img/hero-down.svg"
                alt="hero down icons">
        </div>
    </section>
</template>
  
<script>
  export default {
    name: "HomePage",
  };
  </script>
  
<style lang="scss" scoped>
@use "../assets/styles/partials/variables" as *;

// Section Hero
.hero {
  background-color: #f5f6f7;
  min-height: 450px;
  text-align: center;
  height: calc(100vh - 100px);
}

.hero-first {
  padding: 3rem;

  h2{
    font-size: 1.5rem;
    color: #23CE6B;
  }
}

.hero-img-developer {
  width: 200px;
  height: 200px;
  margin: 20px;
}
</style>
<template>
  <!--<nav id="nav" class="navbar py-4">

    <router-link to="/">
      <a class="navbar-brand ps-5" href="#">
        <strong>Home</strong>
        </a>
    </router-link> 

  </nav>-->
  <router-view />
</template>

<script>
export default {};
</script>

<style scoped>

nav{
  background-color: #353535;  
}

a{
  text-decoration: none; 
  text-transform: uppercase;
  color: #3c6e71; 
}

a:hover{
  color: rgb(113, 103, 247); 
}
</style>
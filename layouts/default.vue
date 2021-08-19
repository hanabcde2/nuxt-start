<template>
  <v-app>
    
    <v-main>
      <v-container>
        <header >
          <h1 class="green--text">{{ $route.name }}</h1>
          <nuxt-link to="/">홈페이지</nuxt-link>
          <nuxt-link to="/Product">Product</nuxt-link>
          
        </header>
        <Nuxt />
      </v-container>
    </v-main>
   
  </v-app>
</template>

<script>

export default {
  data () {
    return {
     
    }
  }
 
}
</script>
<style>

</style>

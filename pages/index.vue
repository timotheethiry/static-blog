<template>
  <div>
    <div id="hero-container" class="h-96 overflow-hidden">
      <img id="hero" class="h-auto
       w-full transform -translate-y-24 mx-auto" src="https://images.unsplash.com/19/nomad.JPG?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=988&q=80" 
           alt="Background image of a mountains view at dawn" />
    </div>

    <div class="flex justify-around my-4 main">
      <ListArticles />
      <Socials />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>

@media screen and (max-width: 700px) {
  
  #hero {
    transform: translateY(0);
  }
  .main {
    display: block;
  }
}

@media screen and (max-width: 550px) {

  #hero-container {
    height: auto;
  }

}
</style>

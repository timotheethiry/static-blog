<template>
    <div>
        <div id="hero-container"  class="h-96 overflow-hidden">
            <img id="hero" class="h-auto
            w-full transform -translate-y-24 mx-auto" src="https://images.unsplash.com/19/nomad.JPG?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=988&q=80" 
            alt="Background image of a mountains view at dawn" />
        </div>

        <section class="my-4 mx-auto p-2 border-2 border-gray-300 shadow-md rounded-lg text-center article">
            <h1 id="title"></h1>
            <!--<p v-for="(tag, index) in article.metadata.tags" :key="index">#{{ tag.sys.id }}</p>-->
            <p id="body"></p>
        </section>
        
    </div>
</template>

<script lang="ts">

    export default {
        data() {
            return {
                article: {}
            }
        },
        created() {
            const contentful = require('contentful');
        
            const client = contentful.createClient({
                space: process.env.SPACE_ID,
                environment: process.env.ENV_ID,
                accessToken: process.env.ACCESS_TOKEN   
            }); 

            client.getEntry(this.$route.params.id)
            .then((entry) => {
                this.article = entry;

                // nuxt fails to render the data inside fields and metadata even though it can render these objects themselves
                const title = document.getElementById('title');
                const body = document.getElementById('body');

                title.textContent = this.article.fields.title;
                body.textContent = this.article.fields.body;

                this.article.metadata.tags.forEach(element => {
                    let tag = document.createElement("p");
                    title.after(tag);
                    tag.textContent = "#" + element.sys.id;
                });
            })
            .catch(console.error);   
        }
    }
</script>

<style scoped>

.article {
    width: 90%;
}

#title {
    font-weight: bold;
}

@media screen and (max-width: 700px) {
        
    #hero {
        transform: translateY(0);
    }
}

@media screen and (max-width: 550px) {

  #hero-container {
    height: auto;
  }
}

</style>
<template>
    <div>
        <div id="hero-container"  class="overflow-hidden">
            <img id="hero" class="h-auto
            w-full mx-auto" :src="photo" 
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
                article: {},
                photo: ''
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
                console.log(this.article.fields.heroImage.sys.id);

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
            .then(() => {
                client.getAsset(this.article.fields.heroImage.sys.id)
                .then((asset) => {
                    this.photo = asset.fields.file.url;
                })
                .catch(console.error); 
            })
            .catch(console.error); 
        }
    }
</script>

<style scoped>

#hero-container {
    height: max-content;
}

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
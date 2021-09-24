<template>
    <div  class="w-8/12 article">
        <div v-for="(article, index) in articles" :key="index" class="mb-4 p-2 border-2 border-gray-300 shadow-md rounded-lg text-center overflow-hidden">
            <div class="mr-auto w-80 float-left object-contain">
                <img class="pr-2 pb-2" :src="previews[index]">   
            </div>
            <div class="h-full">
                <a @click="openArticle(article)"><h2 class="title">{{ article.fields.title }}</h2></a>
                <p v-for="(tag, index) in article.metadata.tags" :key="index">#{{ tag.sys.id }}</p>
                <p class="body">{{ article.fields.body }}</p>  
            </div>
        </div>
    </div> 
</template> 

<script lang="ts">

    export default {
        data() {
            return {
                articles: {},
                previews: []
            }
        },
        methods: {
            openArticle(article) {
                this.$router.push({
                    name: "articles-id",
                    params: {
                        id: article.sys.id
                    }
                })
            }
        },
        created() {
            const contentful = require('contentful');
        
            const client = contentful.createClient({
                space: process.env.SPACE_ID,
                environment: process.env.ENV_ID,
                accessToken: process.env.ACCESS_TOKEN   
            }); 

            client.getEntries({
                content_type: 'blogPost'
            })
            .then((entries) => {
                this.articles = entries.items;
            })
            .then(() => {
                this.articles.forEach(element => {
                    client.getAsset(element.fields.heroImage.sys.id)
                    .then((asset) => {
                        this.previews.push(asset.fields.file.url);
                    })
                    .catch(console.error);
                });  
            })
            .catch(console.error);
            
            
        }
    }
</script>

<style scoped>

.title {
    font-weight: bold;
}

.article {
    margin: 0 1rem 0;   
}

@media screen and (max-width: 700px) {
    .article {
        width: 90%;
        margin: 0 auto 0;
    }
}

</style>
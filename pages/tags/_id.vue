<template>
    <div class="article mx-auto">
        <div v-for="(article, index) in articles" :key="index" class="my-4 p-2 border-2 border-gray-300 shadow-md rounded-lg text-center overflow-hidden">
            
            <a class="cursor-pointer" @click="openArticle(article)">
                <div class="mr-auto w-80 float-left object-contain">
                    <img class="mr-2 mb-2 rounded-lg" :src="previews[index]">   
                </div>

                <div class="h-full">
                    <h2 class="font-bold">{{ article.fields.title }}</h2>

                    <p v-for="(tag, index) in article.metadata.tags" :key="index">#{{ tag.sys.id }}</p>
                    <p class="body">{{ article.fields.body }}</p>  
                </div>
            </a>
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
                'metadata.tags.sys.id[in]': this.$route.params.id
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
    .article {
        width: 90%;
    }
</style>
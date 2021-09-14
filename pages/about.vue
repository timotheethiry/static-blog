<template>
    <div>
        <div v-for="(item, index) in person.items" :key="index">
            <p>{{ item.fields.name }}</p>
            <div class="w-40 h-40 object-contain">
                <img id="photo" :src="photo[index].fields.file.url">   
            </div>
            <p>{{ item.fields.shortBio }} </p>
        </div>
    </div>
</template>

<script lang="ts">

    export default {
        data() {
            return {
                person: {},
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

            client.getEntries({
                content_type: 'person'
            })
            .then((entry) => {
                this.person = entry;
                this.photo = entry.includes.Asset;
            })
            .catch(console.error);   
        }
    }
</script>
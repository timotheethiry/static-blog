<template>
    <div>
        <nav class="p-4 flex flex-wrap justify-center sm:justify-start bg-white border-b-2">

            <!-- top bar left -- merge home with backpack ? -->
            <div class="border-2 p-2 border-gray-300 rounded-lg shadow flex items-center">
                <h1 class="text-gray-700">Backpack with me!</h1>
            </div>

            <ul class="flex py-2 items-center">
                <li class="h-6 mx-6"><nuxt-link class="" to="/">Accueil</nuxt-link></li>
                <li class="h-6 mr-6"><nuxt-link class="" to="/about">Who is this guy ?</nuxt-link></li> 
            </ul>

            <div class="flex items-center py-2 sm:mr-auto"> 
                <button class="h-6 text-base mr-3" @click="toggle(visible)">Tags</button>
                
                <ul class="h-6 list-disc" id="collapse" @click="toggle(visible)">
                    <li class="mx-3"><nuxt-link class="" to="/tags/lorem">Lorem</nuxt-link></li>
                    <li class="mx-3"><nuxt-link class="" to="/tags/ipsum">Ipsum</nuxt-link></li>
                    <li class="mx-3"><nuxt-link class="" to="/tags/dolor">Dolor</nuxt-link></li>
                    <li class="mx-3"><nuxt-link class="" to="/tags/sit">Sit</nuxt-link></li>
                    <li class="mx-3"><nuxt-link class="" to="/tags/amet">Amet</nuxt-link></li>
                </ul>
            </div>

            <!-- top bar right  -->
            <ul class="hidden sm:flex items-center ">
                <li class="h-10 w-10">
                    <img
                        class="h-full w-full rounded-full mx-auto"
                        src="https://images.unsplash.com/19/nomad.JPG?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=988&q=80"
                        alt="profile man" />
                </li>
            </ul>
        </nav>
    </div>
</template>

<script lang="ts">

export default {
    data() {
        return {
            visible: false,
        }
    },
    methods: {
        toggle(visible) {
            const dropdown = document.getElementById('collapse');
            
            if (!visible) {
                dropdown.style.display = "flex";
                this.visible = true;
            } else {
                dropdown.style.display = "none";
                this.visible = false;
            } 
        }
    }
}
</script>

<style scoped>

    #collapse {
        display: none;
        flex-direction: row;
    }

</style>